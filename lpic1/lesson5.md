---
name: lpic
lesson: "5"
topic: systemd, logs
number: "5"
---
Today we gonna learn about the systemd inits and how to config and manipulate them by systemctl, also we gonna learn about journalctl to see the logs.
- as we talked about how the main filesystem boot in linux, we learned that the firmware send a #POST and the bootloader loads #initramfs or #initrd and the kernel loads the init to pass the main duty to it, to load all services and tools and desktop and disk and ... .
##### Definitions:
	systemd: it's a system and service manager in linux that initial and manage       all services .
	unit: each service or device or target or ... that systemd manage it.
	systemctl: in fact it's systemdctl that is a command to manage units.
	init: before of founding systemd, it was the manager but now, the systemd as      modern service and system manager, replaced it.
