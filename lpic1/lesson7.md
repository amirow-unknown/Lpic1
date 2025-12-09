---
name: lpic
topic: Design Hard disk and it's layout
lesson: "7"
number: "7"
---
# FHS(Filesystem hierarchy system) 
	- in linux, file system which called #FHS (filesystem hiarchy system), has directories for different purpose:
	```
	/
	boot 
	lib64
	lib32
	bin -> /usr/bin
	sbin -> /usr/sbin
	mnt
	opt
	root
	etc
	home
	dev
	proc
	srv
	sys
	tmp
	usr
	run
	```
	#boot contains boot files or efi directory which contains efi boot files
	#bin contains non-root commands
	#sbin contains commands for root mode -(the difference of #bin and #sbin is security)
	#mnt you can mount your disk or even removeable disks that system didn't recogize them
	#opt contains the config files of the services that the linux doesn't know them but you installed like nekoray
	#root the #/root contains #root_user home
	#etc configuration files for services
	#home the users the their directories (/home/amir/Desktop)
	#dev contains devices 
	#proc contains process
	#not todays is not much used
	#sys systemd and kernel configuration such as #/sys/class/power_supply for power managment
	#tmp contains temporary files which gonna be empty after each reboot or poweroffing
	#usr secondary hierarchy
	#run it's like #/var directory for services that serves their files and gonna delete after booting or poweroffing
	==Note==:
	- the #/usr directory which is a #secondary_hierarchy, contains the directories in #/ directory such as #bin and #sbin and etc.      Look at this:
	- ls /usr
	`lrwxrwxrwx   1 root root    3 May  3 22:56 sbin -> bin`
	`lrwxrwxrwx   1 root root    3 May  3 22:56 lib64 -> lib`
	`drwxr-xr-x   2 root root 4.0K Aug 16 20:16 lib32`
	`drwxr-xr-x  12 root root 4.0K Sep 22 19:15 local`
	`drwxr-xr-x 193 root root  12K Oct  2 12:29 share`
	`drwxr-xr-x   3 root root 4.0K Oct  5 03:02 src`
	`drwxr-xr-x   6 root root 112K Oct  5 23:41 bin`
	`drwxr-xr-x 379 root root  36K Oct  5 23:41 include`
	`drwxr-xr-x 166 root root 232K Oct  5 23:41 lib`
	comparing #/bin and #/usr/bin :
	- `ls /bin`:2471
	- `ls /usr/bin`:2471
# Disk partition commands:
lsblk -> lists all blocks(loops, devs, disks,swap,...)
mount -> used for #mount and #unmount the disks and also for listing all mounted files,or directories or devices.
parted -> like #fdisk, used for parted command 
- #Swap? imagine you need more *ram* but you don't have money and disks are cheaper, you can use #swap, to use a peace of your disks instead of ram. 
- ==NOTE== -> cause the #disks are slower that #rams, so you can't do process fast same as #ram. but #ssd spaces are better that #disks!   

# swap
- we talked about swap but there are some #tips:
- swap configuration is different in vary distributions:
	#debian and #arch -> swap is a extended partition like /dev/sda5
	#ubuntu it's a swap file that you can see it in / directory
	#redhat it's a virtual device as zram which work like a virtual ram and when you run `swapon` in #redhat you see #/zram0
- swapon -> used for swap configuration command, and if you run `swapon` you see the information of your distro swap:
	`//NAME      TYPE      SIZE USED PRIO`
	`/dev/sdb3 partition  15G   0B   -2`

