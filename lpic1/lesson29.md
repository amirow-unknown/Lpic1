---
name: lpic
lesson: "29"
topic: users and groups access, security files,
number: "29"
---
#### *user and group id's amd their range:*
```bash
0 ==> root ----> can do anything
1-999 ==> system users/services ---> limited than root, like these:
#http:x:33:33::/srv/http:/usr/bin/nologin
#dbus:x:81:81:System Message Bus:/:/usr/bin/nologin
#systemd-coredump:x:980:980:systemd Core Dumper:/:/usr/bin/nologin
#systemd-network:x:979:979:systemd Network Management:/:/usr/bin/nologin
#systemd-oom:x:978:978:systemd Userspace OOM Killer:/:/usr/bin/nologin
#systemd-journal-remote:x:977:977:systemd Journal Remote:/:/usr/bin/nologin
#systemd-resolve:x:976:976:systemd Resolver:/:/usr/bin/nologin
#systemd-timesync:x:975:975:systemd Time Synchronization:/:/usr/bin/nologin 
1000-60000 ===> normal users like me
#nobody:x:65534:65534:Kernel Overflow User:/:/usr/bin/nologin
#amir:x:1000:1000::/home/amir:/usr/bin/zsh
#oxinux:x:1001:1001::/tmp/newme:/usr/bin/bash

```
# *commands:*
###### #useradd ----> to add user
```bash
#to add user by this command, you must be root or a sudoer user.
$root-> useradd oxinux #create oxinux account but not it's home directory
#-m used to make home for user, which /home/username is default
$root-> useradd oxinux -m #creates home directory for oxinux too.
#-d used to determine home path for the user
$root-> useradd oxinux -m -d /tmp/oxinuxhome
#-u --> --uid used to determine user id 
$root-> useradd oxinux -m -d /tmp/oxinuxhome -u 2000
#-g used to determine to add user in which group
#-G used to determine to add user in secondary groups
$root-> useradd -m -d /tmp/oxinux -u 2000 -g oxinux -G amir,docker,wheel oxinux
#-s to determine shell 
$root-> useradd -m -d /tmp/oxinux -u 2000 -s /bin/zsh
#-c to add comment for a user
$root-> useradd -m -u 2000 -c "newuser" mahan
#-e to define expire time for the user
$root-> useradd -m -e 2025-02-12 -c "temporary" -u 2004 oxinux
#NOTICE 
#when you user useradd with no switches, it uses it's default values! but from where?
$amir-> useradd -D
#you can change some of them
$amir-> useradd -D -s /bin/zsh
```
###### #userdel ----> to delete user
```bash
#using only 'userdel' remove useraccount not it's mailpool or home directory
$root-> userdel oxinux
#-r used to remove also user home directory and mail pool
$root-> userdel -r oxinux #if you created other stuff except it's home, you must search for them to delete remove them
#-f use force to remove user by force, rarely while user has some running process
$root-> userdel -r -f oxinux
#alo you can use this command first and then remove the user
$root-> killall -u oxinux
$root-> userdel -r oxinux
#first kills all oxinux process, then delete and remove it and it's home and mail
```
###### #usermod ---> modifying user 
```bash
#-aG used to add user to secondary groups
$root-> usermod -aG wheel,docker oxinux
#if you use only -G not -aG you remove all existing secondary groups and add your groups, -a called append
$root-> id oxinux 
#uid=2000(oxinux) gid=998(wheel) groups=998(wheel),966(docker)
$root-> usermod -G wheel,amir oxinux
#uid=2000(oxinux) gid=998(wheel) groups=998(wheel),966(amir)
#-g used to change primary group
$root-> usermod -g root oxinux
#uid=2000(oxinux) gid=0(root) groups=998(wheel),966(docker)
#to change the user comment
$root-> usermod -c "i changed" oxinux 
#-d used to change user home directory path, but doesn't move the content from last home directory to new
$root-> usermod -d /path/path oxinux
#-m -d, fix the issue of only -d
$root-> usermod -m -d /path/path oxinux
#-s to change the user shell
$root-> usermod -s /bin/zsh oxinux
#-u to change user UID
$root-> usermod -u 500 oxinux
#-l to change user's name
$root-> usermod -l jadi oxinux #---> changed oxinux to jadi
#-e to add expiration time 
$root-> usermod -e 2025-11-12 jadi
#how to disable!!!!
$root-> usermod -e "" jadi
#-L to lock user-> a ! appears in /etc/shadow file for user and user cannot login but root.
#use -U to unlock it
$root-> usermod -L/-U jadi
```

###### #chage ---> change user password expiry information
```bash
#-l ---> shows user information
Last password change					: Nov 27, 2025
Password expires					: never
Password inactive					: never
Account expires						: never
Minimum number of days between password change		: 0
Maximum number of days between password change		: 99999
Number of days of warning before password expires	: 1
#password expire ----> date to password expiry
#account expire ---> like above
# warning expire ---> ... days before expiration to change password
------------
#-E ---> add accout expiration date
```
###### #passwd ---> password modification and login modification
```bash
#-s to see user status
jadi P 2025-11-28 0 99999 1 -1
jadi:username
P: status
	P ---> useable password
	NP ----> no passwd
	L ----> locked password
2025-11-28: last date password changed
0: minimum age
99999: maximum age
1: warning period day
-1: inactivity period which is -1
#change password
$amir-> passwd amir
-----------
# -e to force user to set new pass for next login
$root-> passwd -e jadi
# -l to lock user password, user cannot login:)
# -u to unlock
$root-> passwd -l/-u jadi
#-d to delete password of account, only root can login
$root-> passwd -d jadi && su jadi

```
###### #groupadd --> adding group
```bash
#adding new group
$root-> groupadd groupname
#-g to set guid
$root-> groupadd -g 1010 groupname
#-r used to create system group
$root-> groupadd -r groupname
#-p to set password
$root-> groupadd -p password groupname
```
###### #groupdel ---> deleting group
 ```bash
#groupdel groupname ===> remove group
$root-> groupdel mamlian 
 ```
###### #groupmod ---> modifying groups
```bash
#-n to change group name
$root-> groupmod -n newname oldname
#-g to change GID
$root-> groupmod -g 999 groupname

```

###### #imporant_files ---> /etc/shadow && /etc/passwd
- ***/etc/passwd*** -----> users information
	`cat /etc/passwd | grep root`
		`root:x:0:0::/root:/usr/bin/bash`
		:x -> password which passwd file doesn't show
		0 ---> UID
		0 ---> guid
		/root ---> home
		/usr/bin/bash ---> shell
- /etc/shadow ---> users passwords(hashed)
- `sudo cat /etc/shadow | grep amir`
```bash
amir:$y$j9T$.lrUtRdpHydhCAZVsBhoZ/$m8jVGHaQA7r1pNqXg4dbrOiFpCKozbn2v5LXjB8LWT8:20279:0:99999:7:::

amir ---> username
20279 ---> last time password changed
7 ----> waning period day
$y$j9T$.lrUtRdpHydhCAZVsBhoZ/$m8jVGHaQA7r1pNqXg4dbrOiFpCKozbn2v5LXjB8LWT8 ---> hashed password
	bluefish
	bluefish
	sha256
	sha512
	yescrypt
  ```
  