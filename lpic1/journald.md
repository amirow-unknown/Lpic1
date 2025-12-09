---
name: lpic
topic: journald and journalctl
---
-  as we know, systemd is getting bigger each day and works on various parts of systems, such as managing units, services, timers, .....
- one of these actions which is important, is it's service named #systemd-journald.service whic logs all things and manage them, and then save them in **.journal** format files which is **binary** and are only readable by it's utility which is #journalctl.

- ***Tip*** ---> by using journald. you don't need to logrotate and rsyslog configuration!
----
# *how systemd-journald.service manages logs?*
- #### ***log Files managing:***
journald service has a field in it's conf file named #storage, which indicates to how save the log files!
- journald get's logs and have some options:
	- if there were no disks, save them in ram which is not persistent.
	- if there was a disk and there was directory **/var/log/jourrnald/machine-id**, save each logfile there.
	- if there was a disk and there was no directory **/var/log/journald/machine-id**, create this **directory and save files there**
	- **another option is to log nothing**
==Storage=none== ------> doesn't log anything
==Storage=auto== -------> if there was the directory **/var/log/journal/machine-id** save file, and don't if there wasn't
==Storage=volatile== -----> save logs in ram ---> **not persistent method**
==Storage=persistent== ----> save logs in **/var/log/journal/machine-id** and if there wasn't, create and save there.
- *Tip* => machine-id is a id of your machine(system) which is unique in universal and journald uses it to create log directory for your system, look at this:
```bash
$amir-> cat /etc/machine-id
6e5ae02a8a31413f8b7424d5d5a0c4ff
$amir-> ls /var/log/journal/
6e5ae02a8a31413f8b7424d5d3n0c4ff  remote
```
---
### ***journald configuration:***
main config file is on **/etc/systemd/journald.conf** which indicates how manage logging.
```bash
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it under the
#  terms of the GNU Lesser General Public License as published by the Free
#  Software Foundation; either version 2.1 of the License, or (at your option)
#  any later version.
#
# Entries in this file show the compile time defaults. Local configuration
# should be created by either modifying this file, or by creating drop-ins in
# the journald.conf.d/ subdirectory. The latter is generally recommended.
# Defaults can be restored by simply deleting this file and all drop-ins.
#
# Use 'systemd-analyze cat-config systemd/journald.conf' to display the full config.
#
# See journald.conf(5) for details.

[Journal]
Storage=auto
#storage field, indicates to how save the logs!
#Compress=yes
#Seal=yes
#SplitMode=uid
#SyncIntervalSec=5m
#RateLimitIntervalSec=30s
#RateLimitBurst=10000
SystemMaxUse= -----> maximum disk usage, default space is 10%
SystemKeepFree= ----> keep at least NUM much free
SystemMaxFileSize= ----> maximum size for each file
SystemMaxFiles= ----> maximum counts of files not more than this number
#keeping log files in memory has blow options equals to above options:
RuntimeMaxUse= ----> maximum disk usage, 10% is default
RuntimeKeepFree= ---> keep at least NUM much free
RuntimeMaxFileSize= ---> maximum files size
RuntimeMaxFiles= ---> maximum counts of files
#MaxRetentionSec=
#MaxFileSec=1month
#ForwardToSyslog=yes
#ForwardToKMsg=no
#ForwardToConsole=no
#ForwardToWall=yes
#TTYPath=/dev/console
#MaxLevelStore=debug
#MaxLevelSyslog=debug
#MaxLevelKMsg=notice
#MaxLevelConsole=info
#MaxLevelWall=emerg
#LineMax=48K
#ReadKMsg=yes
#Audit=no
```
---
# *Trick for you, if your system crashed*
- if imediately your system(linux) crashed, do this:
remove your disk(has log files) and connect it to another system.
mount it and looks for **/mnt/newdisk/var/log/journal**.
use ***sudo journalctl -D /mnt/newdisk/var/log/journal/machineid***
- -D ---> giving absolute path of journal files
- --file ---> giving one special log file (amir292j298ej2ie.journal)
- --merg ----> merging the log files to current log files 
- --root ---> if you didn't find where are the log files in disk, use --root and path to this (journalctl --root /mnt/newdisk)
---
# logger or systemd-cat ? :))
- we had logger for rsyslog, and now we have systemd-cat to send log:
  - **systemd-cat ls** ---> writes ls command stdout and you can see by `journalctl -e`
  - systemd-cat -p err hello --> writes hello to error priority and you can see by `journalctl -p err`
  these are levels of pririty which we said before:
	- 0 ---> emerg
	- 1 --> alert
	- 2 --> crit
	- 3 --> error
	- 4 --> warning
	- 5 --> notice
	- 6 --> info
	- 7 --> debug
---
# *switches of journalctl *
- #systemd-cat ----> sending log
- #journalctl -r ---> shows logs reverse
- #journalctl -f ---> following mode
- #journalctl -e ---> shows end
- #journalctl -n ... ---> shows N lines from end
- #journalctl -k ---> equals dmesg
- #journalctl --list-boots ---> list the recent boot log(dmesg)
- #journalctl -b bootnumber ---> dmesg of that boot log
	- by default returns last boot log
- #journalctl -p ---> indicating priority
	- range of priority by 1..3 or 3..7 or ...
- #journalctl -u --> indicating the wanted unit
- #journalctl --since / --until ---> defining time range
- #journalctl  --no-pager ----> display result as stdout not in less or other tools
- #journalctl -x ---> more information
- #journalctl --disk-usage ---> shows how much logs takes of disk usage
- 