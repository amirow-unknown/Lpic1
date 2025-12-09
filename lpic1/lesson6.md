---
name: lpic
lesson: "6"
topic: systemd run levels
number: "6"
---
different run levels in systemd: there are different run levels of systemd which you can use them to change your runlevels by command `systemctl isolate ...`, but `isolate` flag has some different modes:
1- rescue -> disable muli-user and graphical modes and limition on commands and files.
	==multi-user: the systemd only knows root==
2- emergancy -> like rescue and disconnect network
3-halt -> disable all targets and units like poweroff command but doesn't disconnect power in pc, so if your pc has LED or lamp they not gonna turn off.
3- poweroff -> shudown mode
#### Shutdown command: `shutdown flag time wall`
- shutdown -> this command is systemctl command that includes `reboot -r, poweroff -P, halt -H`
- flags -> reboot -r, poweroff -P, halt -H, cancelling -c, --show shows the shutdown schedule.
- time -> hour:minutes -> `shutdown -r 4` -> reboot in 5 minutes later.
- wall -> wall is a command that send notificatio to other user, in `shutdown` command it used to notify other users about shuttingdown,
- --show -> shutdown --show -> shows shutdown schedule and if no schedule has setted, you get `No schedule shutdown` error.
# NOTE: 
	The /etc/motd file, you can write anything that if someone used ssh      to connect to your pc, that message appears
