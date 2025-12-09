---
name: lpic
lesson: "3"
topic: hardware and kernel modules it's commands
number: "3"
---
- there are some commands to list your hardware.
- #lsblk -> lists all blocks that save your data such as loops and hards or usbs.
- #lspci -> lists all connected harware by pci in your motherboard.
- #lshw -> lists any hardware of your system by deeply.
- #lsusb -> lists all connected devices by any type of usb 

## kernel and modules!
in windows you must install each driver of your hardware seprately and configure it. but in linux the kernel it's self has each hardware configuration as module file by format #ko such as **filename.ko** and the neccesary ko files load while booting the system and others load when needed. but how can we see this modules?
- #lsmod -> lists all modules that currently loaded by details like *module name*, *used by how many client*, *by who*
- #rmmod -> to remove a module you can use this like **sudo rmmod iwlwifi**
	- flag -f used to force remove a module
- #insmod -> to reinsert the module you must know the exact path of module like this **insmod path/to/module/filename.ko**
- #modprobe  -> but we have not time to find module file. so use #modprobe to automatically find and insert the module => **sudo modprobe iwlwifi**
	- flag -r used to unload a module.
- #modinfo -> used for get details of a module. ***details such as it's path***
main difference of #modprobe  and #rmmod and #insmod is that the #modprobe load the last version and convenient version of module but in #inmod and #rmmod you must specifice your module and it's path.
## how to find the path of modules?!
the default and commen path is */lib/modules/....*. but cause all modules are not in one directory you can use #modinfo command to find exact path of a module. for example the path of *video* module is **/lib/modules/6.15.9-arch1-1/kernel/drivers/acpi/video.ko.zst**

## directories
/etc/module.d -> the list of module that you set to load while booting
/etc/modprobe.d -> settings of your configured modules in /etc/module.d file.


