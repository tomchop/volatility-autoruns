# Volatility autoruns plugin

Finding persistence points (also called "Auto-Start Extensibility Points", or ASEPs) is a recurring task of any investigation potentially involving malware.

To make an analyst's life a bit easier, I came up with the `autoruns` plugin. `autoruns` basically automates most of the tasks you would need to run when trying to find out where malware is persisting from. Once all the autostart locations are found, they are matched with running processes in memory.

## Roadmap

* Extra ASEPs: Scheduled tasks (done!), Startup folders
* OS X / Linux support
* Performance optimizations

## ASEPs list

**Software hive**

* "Microsoft\Windows\CurrentVersion\Run",
* "Microsoft\Windows\CurrentVersion\RunOnce",
* "Microsoft\Windows\CurrentVersion\RunServices",
* "Microsoft\Windows\CurrentVersion\Policies\Explorer\Run",
* "Wow6432Node\Microsoft\Windows\CurrentVersion\Run",
* "Wow6432Node\Microsoft\Windows\CurrentVersion\RunOnce",
* "Wow6432Node\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run",
* "Microsoft\Windows NT\CurrentVersion\Terminal Server\Install\Software\Microsoft\Windows\CurrentVersion\Run",
* "Microsoft\Windows NT\CurrentVersion\Terminal Server\Install\Software\Microsoft\Windows\CurrentVersion\RunOnce"

**NTUSER.DAT hives**

* "Software\Microsoft\Windows\CurrentVersion\Run",
* "Software\Microsoft\Windows\CurrentVersion\RunOnce",
* "Software\Microsoft\Windows\CurrentVersion\RunServices",
* "Software\Microsoft\Windows\CurrentVersion\RunServicesOnce",
* "Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run",
* "Software\Microsoft\Windows NT\CurrentVersion\Terminal Server\Install\Software\Microsoft\Windows\CurrentVersion\Run",
* "Software\Microsoft\Windows NT\CurrentVersion\Terminal Server\Install\Software\Microsoft\Windows\CurrentVersion\RunOnce",
* "Software\Microsoft\Windows NT\CurrentVersion\Run",
* "Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run",
* "Software\Wow6432Node\Microsoft\Windows\CurrentVersion\Run"

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
* 
** Scheduled Tasks **

* C:\Windows\System32\Tasks\ (Windows Vista and onwards only)

