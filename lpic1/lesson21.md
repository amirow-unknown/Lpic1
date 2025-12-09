---
name: lpic
lesson: "21"
topic: maintain the integrity of filesystem
number: "21"
---
## commands:
#df ---> shows information of block devices
```bash
df -h /dev/sdb1 --> -h --> human readable
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       488M  239M  249M  49% /boot

df -hT /dev/sdb1 ---> -T --> shows filesystem type
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdb4      ext4  155G   17G  130G  12% /home

$ sudo fdisk -l /dev/sdb | grep -e "/dev/sdb[0-9]" -o | xargs -I X bash -c "df -hT X"

Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdb1      vfat  488M  239M  249M  49% /boot
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdb2      ext4   49G   35G   12G  76% /
Filesystem     Type      Size  Used Avail Use% Mounted on
devtmpfs       devtmpfs  3.9G     0  3.9G   0% /dev
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdb4      ext4  155G   17G  130G  12% /home
```
#du ---> shows information of direcory space
```bash
#du command
du -h /home/amir/Desktop
16K	/home/amir/Desktop/learningo
40K	/home/amir/Desktop
#switch s in du command
du -hs /home/amir/Desktop
40K	/home/amir/Desktop
#swtich c and --max-depth in du command
du -hc ---> -c ---> total space
du --max-depth /path---> explore files and directories of given path but in the level which you give by --max-depth

sudo du --max-depth 1 /home/ 
17775260	/home/amir
16	/home/lost+found
17775280	/home/

 sudo du --max-depth 2 /home/
448	/home/amir/dropbox
12	/home/amir/.yandex
23768	/home/amir/.vscode
1526340	/home/amir/go
124680	/home/amir/Downloads
1307156	/home/amir/.rustup
466340	/home/amir/.thunderbird
817412	/home/amir/.local
142300	/home/amir/snap
16	/home/amir/.ssh
4224	/home/amir/Pictures
16	/home/amir/.android
40	/home/amir/Desktop
2170112	/home/amir/.cache
25600	/home/amir/.oh-my-zsh
6490152	/home/amir/Document
4	/home/amir/phone
3176	/home/amir/.vscode-oss
296836	/home/amir/snapd
755460	/home/amir/.mozilla
4	/home/amir/Public
220	/home/amir/.purple
8	/home/amir/Amir_cronjobs
20412	/home/amir/.cargo
```

#fsck ---> to check your storages healthy and their info, imagine after the power gone, you don't know that your files is copied or not or correpted or .....
```
ext ---> tune2fs ==> Show or set ext2 and ext3 parameters or even set the journaling options|

ext ---> dumpe2fs ==> Prints the super block and block group descriptor information for an ext2 or ext3 filesystem.

ext ---> debugfs ==> Is an interactive file system debugger. Use it to examine or change the state of an ext2 or ext3file system.

reiserfs --> reiserfstune ==> show and set parameters

reiserfs --> debugreiserfs ==> Prints the super block and block group descriptor information for an ext2 or ext3 filesystem.

XFS --> xfs_info ==> display information
XFS --> xfs_growfs ==> expand file system
XFS --> xfs_admin ==> change parameters on XFS file systems
XFS --> xfs_repair ==> repair the problems
XFS --> xfs_db ==> checks and debugs the filesystem
```
---
# Filesystem table:
- in linux, there is a file which is #fstab that is on ***/etc/fstab*** path. it contains the #UUID of each block file and their udev name and the mount point and ...
  
```bash
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
  -  so you can mount your blocks by this file too and add some other configs!
