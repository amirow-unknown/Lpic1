---
name: lpic
lesson: "20"
topic: creating, modifying and etc of partitioning
number: "20"
---
- *what is a block device*  --> a #block_device is a nonvolatile storage device which when your system boots, it's data gonna not lost like #RAM,  and can be accessed by any order such as hdd, ssd, nvm, usb flash, hard external and so on... .
- as we said, we have two types of firmware: #Bios or #uefi --> Bios use #MBR and Uefi use #gpt.
- linux, use #udev to add device and their partitions to /dev and sort them, such as /dev/sda1, /dev/sda2, ....
- 
- # commands:
	*fdisk:* used for #MBR 
	*gdisk:* used for #gpt 
	- both are almost like each other, but here we learn #fdisk cause i use #bios 
##### #Fdisk:
- #lsblk ---> lists the block devices
- #fdisk /dev/sda ----> the menue of sda in fdisk to partitioning
- #fdisk -l /dev/sda ---> shows the partion info of /dev/sda
	- -a ---> to toggle a partition for bootable flag
	- -m ----> menue, which shows all shortkey of #fdisk 
	- -p ---> shows the partition table
	- -n ---> create new partition
	- -t ---> set the type of partition which, the created partition is #linux already.
	- -d ---> to delete a partition
	- -l ---> shows the avaible types of partition to set on partition
	- -v --> verify to look that there are no issues
	- -i ---> shows information of selected partition
	- -w ---> write and exit
	- -q ---> exit without no changes
# Tip:
- *difference of #Primary and #extended partition?*
	in #MBR, you can only 4 Partitions, so if you need more partitions, what you gonna do??
	you can use one of these 4 partitions as #extended, and then you can create new partitions.
	- in fact, new more partitions spaces, are under the #extended partition.
	- #EXAMPLE:
		- you have 2 partitions and now you wanna have 3 other partitions:
		  1- set third partition as #extended 
		  2- now if you add another partition, it's partition number gonna be 5. why!!!???
			  cause you coud have only 4 partitions! yes??
				  so you create third partition extended which means you gonna have more partitions which gonna be numbered from 5!
				  something like this:
				   Device         Start       End   Sectors   Size Type
				   /dev/sdb1       2048   1001471    999424   488M EFI System
				   /dev/sdb2    1001472 105859071 104857600    50G Linux filesystem
				   /dev/sdb3    105859071 145859071 105859071  2G extended
				   /dev/sdb5    .....            .....            .....                   1G linux
				   /dev/sdb6    .....           ...             ......                    1G linux

# Filesystems:
after you partitioned your storage, you need to format each partition to a #File_system.
but why we need to format!---> after partitioning, you need to make a map of each partition and their locations and uuid for each partition to save your data such as files and directories in blocks of spaces and access them by those maps and links.

- ***list of filesystems:***
	ext2 ----> it's old format type, don't support journaling.
	ext3 --> upgrade version of #ext2 which has journaling and support only 2TB max file size and 16 TB. 
	ext4 --> high performance than #ext3 and support only 16TB max file size and 1 EB(1000*1000TB) 
	XFS ---> has journaling and cache in ram, most used in servers, to have more compaibility and support 8EB filesystem max size.  
	vFAT --> hasn't journaling, and don't know permissions and symlinks, most used in windows, and is popular for it's knowning in most of devices.
	exFAT ---> extended version of vFAT, most used in usb disks.
	btrfs ----> support LVM and RAID and snapshotss and high performance
	swap ---> using disk space as ram

- ***note--->***
	***LVM-->*** to combine some storage and create new partitions which are parts of different storage.
	***VFAT and exFAT--->*** because of their more usage in tech, most of usb disks are formatted by this format. cause if you format your usb disk by another types like ext4 or..., it's possible that if you insert it in a different hardware, it doesn't recognize it, but most hardwares know #vfat and #exfat
## commands
#mkfs ---> to format you partitions:
`mkfs -t ext4 /dev/sda1` ---> format /dev/sda1 to ext4 filesystem

#blkid ---> to get info such as UUID and ... about your partitions
`blkid /dev/sda1` -> `/dev/sdb3: UUID="eb83f1eb-25d0-4ef7-b064-e44d51ec0fdf" TYPE="swap" PARTUUID="161f7491-7270-48aa-b6bf-21dc6021a1b2"`

`blkid /dev/sda` -> `/dev/sdb: PTUUID="ac59b0dd-9d41-4637-b237-4ace3de8eb2d" PTTYPE="gpt"`

#mkswap --> to format your partition to swap filesystem type.
`mkswap /dev/sda4`
