---
name: lpic
lesson: "2"
topic: hardware
number: "2"
---
- today we gonna learn about directories /sys /dev /proc and what do they do!
/sys -> is a psudo file system that give you information about your hardware and you can also modify them. these files comes from kernel's memory.

/dev -> here you see the hardware information as virtual file system that applications and users can use these file system to interact with hardware.

/proc -> all of the process are in this directory, you can even use #more command to see the process details. when i run #ps command, those process numbers are in the /proc directory.

- you can change your power setting in /sys/class/power_supply directory. but you can't see any file of power setting in /dev cause *only hardware with direct I/O operations are in /dev directory*.
 - if you run *ping google.com &* in background and run *ps* command see it's process id,  you can find it and get it's information in /proc directory and kill it by *kill #Process_id*
## the diffrence of /sys , /dev, /proc
- the /proc and /dev, both are virtual filesystem and you can manipulate any thing by these directory, /dev is for device information and /proc is for kernel process and other running process
- you can use /sys to manipulate:
	- /sys/block -> for harddisk and storages
	- /sys/bus -> pci, usb, slats
	- /sys/class -> list of hardware to change their config directly.
