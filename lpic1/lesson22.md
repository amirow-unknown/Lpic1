---
name: lpic
lesson: "22"
topic: mounting and unmounting block devices
number: "22"
---
- after you #partitioned your block devices and then #formatted in a type of those filesystem formats, you must mount you're partitions.
### example:
- imagine the space of your home, is out of running and you need more space, so you insert new #HDD or #ssd and partition and formate it. now you can run a command like this `sudo mount /dev/sdx /home/amir` , after doing this, amir home space increase.

# Command
#mount ---> mounting and unmounting
	mount --> shows all mounted devices and their path
	mount -t .... ---> dedicating the block device format.
#unmount ---> opposite of mounting
	`sudo unmount /dev/sdx`
	or --> `sudo unmount /path/of/dev/sdx`
#swapon ---> to mount the swap
#swapoff ---> opposite of #swapon 
## Tips:
- when a partition or device is in use, you can't unmount it but:
- `mount -l ...` ---> ***lazy mode*** --> unmount slowly and step by step, first start from unused partitions.
- `mount -f ...` ---> ***fuck you bitch*** ---> it's in force mode and don't give a fuck about you.
 - **to unmount you can run `unmount /dev/sdx` or `unmount /pathofmounteddirectory`** 
 - ***to mount and unmount the #Swap you can use command #swapon and #swapoff***
---
# UUID & LABLE
### #uuid or (universal unique identifier):
imagine you have disk which you use it sometime and after each using, you unmount it, so if sometime it's udev name could be changed to another one such as `/dev/sda` to `/dev/sdh`, also you want to have not changeable name of your disk, so use it's #UUID, use command `lsblk -o +uuid / blkid` to see it's UUID and run `mount/unmount UUID=uuidofit`.
- also you can use it's LABLE but the UUID is most better option to use.
now imagine you wanna that each time you connect your disk to laptop, it's automatically recognize it and mount it. you can use **fstab file**
- **fstab is a file which contains some blocks and their UUID and type and path of mount which mount them each time the system boots.**
- ```bash
  # Static information about the filesystems.
# See fstab(5) for details.

# <file system> <dir> <type> <options> <dump> <pass>
# UUID=5db013b6-f967-4935-8c30-d5e5180a9590
/dev/sdb2           	/         	ext4      	rw,relatime	0 1

# UUID=91bd898f-9c2a-478b-aab8-84dd304e1d3d
/dev/sdb4           	/home     	ext4      	rw,relatime	0 2

# UUID=9501-7AD2
/dev/sdb1           	/boot     	vfat      	rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=ascii,shortname=mixed,utf8,errors=remount-ro	0 2

# UUID=eb83f1eb-25d0-4ef7-b064-e44d51ec0fdf
/dev/sdb3           	none      	swap      	defaults  	0 0
/dev/sda                /mnt/MY_DISK    ext4            rw,relatime     0 0
  ```
*it's structure:*
`pathofblock`    /mount point     type      rw/defaults       0 0 
- also you can use `user or root` option to determine that users has permission to mount or unmount it or not.
- after you set your info, boot the laptop or mount your disk by this method --> `mount /pathofmount`
-