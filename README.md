# Volatility autoruns plugin

[![Build Status](https://travis-ci.com/tomchop/volatility-autoruns.svg?branch=master)](https://travis-ci.com/tomchop/volatility-autoruns)



Finding persistence points (also called "Auto-Start Extensibility Points", or ASEPs) is a recurring task of any investigation potentially involving malware.

To make an analyst's life a bit easier, I came up with the `autoruns` plugin. `autoruns` basically automates most of the tasks you would need to run when trying to find out where malware is persisting from. Once all the autostart locations are found, they are matched with running processes in memory.

## How-to

The plugin is pretty straightforward to use. The folder where the plugin is located should be passed on to Volatility using the `--plugins=` parameter.

Relevant options for the plugin are:

* `-v` or `--verbose` - Shows extra information that would normally be filtered (like Services from the System32 folder)
* `-t` or `--asep-type=[autoruns|services|appinit|winlogon|tasks|activesetup]` - Use it to focus on specific ASEPS. Options are: `autoruns` (Run, RunOnce, etc.), `services`, `appinit`, `winlogon`, `tasks`, and `activesetup`. You can specify any combination of them with a comma-separated list: `autoruns,services`. Leave blank to get all ASEPs.
* `--output=[text|table|json]` - table will output the text in a table format (less readable but somehow more consice). The default output mode is text, where more information is avialable. json option produces the unified json output format. 

## Roadmap

* Extra ASEPs: Scheduled tasks (done!), Startup folders
* OS X / Linux support
* Performance optimizations

## ASEPs list

**Software hive**

* Microsoft\Windows\CurrentVersion\Run,
* Microsoft\Windows\CurrentVersion\RunOnce,
* Microsoft\Windows\CurrentVersion\RunServices,
* Microsoft\Windows\CurrentVersion\Policies\Explorer\Run,
* Wow6432Node\Microsoft\Windows\CurrentVersion\Run,
* Wow6432Node\Microsoft\Windows\CurrentVersion\RunOnce,
* Wow6432Node\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run,
* Microsoft\Windows NT\CurrentVersion\Terminal Server\Install\Software\Microsoft\Windows\CurrentVersion\Run,
* Microsoft\Windows NT\CurrentVersion\Terminal Server\Install\Software\Microsoft\Windows\CurrentVersion\RunOnce

**NTUSER.DAT hives**

* Software\Microsoft\Windows\CurrentVersion\Run,
* Software\Microsoft\Windows\CurrentVersion\RunOnce,
* Software\Microsoft\Windows\CurrentVersion\RunServices,
* Software\Microsoft\Windows\CurrentVersion\RunServicesOnce,
* Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run,
* Software\Microsoft\Windows NT\CurrentVersion\Terminal Server\Install\Software\Microsoft\Windows\CurrentVersion\Run,
* Software\Microsoft\Windows NT\CurrentVersion\Terminal Server\Install\Software\Microsoft\Windows\CurrentVersion\RunOnce,
* Software\Microsoft\Windows NT\CurrentVersion\Run,
* Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run,
* Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Run

**Winlogon & AppInit**

* Microsoft\Windows NT\CurrentVersion\Winlogon (value AppInit_DLLs)
* Microsoft\Windows NT\CurrentVersion\Winlogon\Notify
* Microsoft\Windows NT\CurrentVersion\Winlogon\Notify
* Microsoft\Windows NT\CurrentVersion\Winlogon\Userinit
* Microsoft\Windows NT\CurrentVersion\Winlogon\VmApplet
* Microsoft\Windows NT\CurrentVersion\Winlogon\Shell
* Microsoft\Windows NT\CurrentVersion\Winlogon\TaskMan
* Microsoft\Windows NT\CurrentVersion\Winlogon\System

**Services**

* CurrentControlSet\Services

**Scheduled Tasks**

* C:\Windows\System32\Tasks\ (Windows Vista and onwards only)

**Active Setup**

* Microsoft\Active Setup\Installed Components

**Microsoft Fix-it**

* Microsoft\Windows NT\CurrentVersion\AppCompatFlags\InstalledSDB


