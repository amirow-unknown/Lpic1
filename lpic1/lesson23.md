---
name: lpic
lesson: "23"
topic: users, groups, permissions
number: "23"
---
## ***Commands:***
#whoami ----> shows the user of running the command(such as root or amir)
 ```bash
#amir is the current user
  $ whoami
  amir
  #root is the current user
  \# whoami 
  root
  ```
#groups ---> shows the groups of the user which is in(such as wheel, root(if setted),...)
- ```bash
  #amir is the current user
  $ groups
  amir wireshark wheel
  #root is the current user
  \# groups
  root
  ```
#id ---> shows the ID's of user
- ```bash
  #amir is the current user
  $ id
  uid=1000(amir) gid=1000(amir) groups=1000(amir),150(wireshark),998(wheel)
  #root is the current user
  \# id
  uid=0(root) gid=0(root) groups=0(root)
  #definition of UID and GID and GROUPS
  uid ---> user ID
  gid ---> the group of user which most of time is the name of the user->(ali ali)
  group ---> the groups of the user which is in there
  ```
#chmod ---> modifying the permission of files and directory
- At first we must know the number of each permission:
	- x(execute) ---> 1
	- w(write) ----> 2
	- r(read) ---> 4
	- #so:
	- rw- ==> 6
	- r-x ==> 5
	- rwx ==> 7
	- -wx ==> 3
	- --- ==> 0
```bash
$amir-> nvim amir.sh
#no one even root and amir cannot run it cause it's permission is -rw-r--r--
#so amir runs chmod command to get permission
$amir-> chmod 751 amir.sh
#definition
7 -> read+write+execute for the owner of file which here is amir
5 -> read+execute for the members of group amir
1 -> only execute for others
#there are some other methdos:
$amir-> chmod +x ===> users of amirgroup can execute
$amir-> chmod u+wx ===> user can write and execute 
$amir-> chmod u+wxr ===> user can write+execute+read
$amir-> chmod u+xr,g+xr,o+x ===> user can execute+read and group of amir group can execute+read and other can execute
$amir-> chmod g+xr ===> amirgroup can execute and read

also to get these permission you can use -(mines) instead of +(pluse):
$amir-> chmod o+rx amir.sh
-rwxr-xr-x amir.sh
$amir-> chmod o-r amir.sh
-rwxr-x--x amir.sh 
```
- ***switch -R*** ---> set the permission to all files and directories in a directory or path
```bash
$amir-> chmod -R 777 folder
$amir-> chmod -R 555 .
```
#chown ---> used to change the owner and group of files and directories
```bash
$amir-> ls -lrth
-rwxr-xr-x amir:amir amir.sh
$amir-> chown root:amir amir.sh
$amir-> chown amir:wheel amir.sh
$amir-> chown :root amir.sh
```
- ***switch -R*** ---> like chmod, it's a recursive switch.`$amir-> chown amir:wheel .`
#chrgrp ----> used to change the groups of files and directories
```bash
$amir-> chgrp wheel new
$amir-> chgrp -R root .
```
- ***switch -R*** ---> it's recursive like command chmod and chown!
#usermod ----> used to modifying user account
- swtich -aG
```bash
$amir-> sudo usermod -aG root amir #adds amir to root group
```
#newgroup ----> login new group
```bash
$amir-> id
uid=1000(amir) gid=1000(amir)
$amir-> group
amir wheel root
$amir-> touch new
$amir-> ls -l
-rwxr-xr-x amir:amir ----> #the group is amir cause it's main group is amir
$amir-> newgrp wheel
$amir-> id
id=1000(amir) gid=998(wheel)
$amir-> touch new
$amir-> ls -l
-rwxr-xr-x amir:wheel new #the group is wheel cause i changed my main group to wheel
```
#unmask 
```bash
$amir-> umask
#002
#means all files and directories you create has 666-002=664 permission, means
#664 ---> user(rwx),group(rwx),other(r)
#to change umask use this, and of course it's so strick! :) 
$amir-> umask 055 
#also you can set like this:
$amir-> umask u=rwx,g=xr,o=x
```

---
## ***Tip's:***
- for each user which created in linux, a group will be maken for it --> amir(user), amir(group)
- Difference between ***sudo su, sudo -s, su -***
	- sudo su ---> ***gives root shell and also remains the last user shell environment variables***
	- sudo -s ----> ***like abow but, doesn't remain the last user shell environment variables***
	- su ---> ***used to change between users*** => `su amir--> $amir` , `su root` or `su -` --> `#root`
- ID(user id) 0 is reserved as root's id

---
## ***File's:***
#/etc/passwd ---> contains users information and ....
```bash
$ sudo cat /etc/passwd
root:x:0:0::/root:/usr/bin/bash
bin:x:1:1::/:/usr/bin/nologin
daemon:x:2:2::/:/usr/bin/nologin
mail:x:8:12::/var/spool/mail:/usr/bin/nologin
ftp:x:14:11::/srv/ftp:/usr/bin/nologin
http:x:33:33::/srv/http:/usr/bin/nologin
nobody:x:65534:65534:Kernel Overflow User:/:/usr/bin/nologin
amir:x:1000:1000::/home/amir:/usr/bin/zsh
#definition
amir:x:1000:1000::/home/amir:/usr/bin/zsh ---> username is amir,x: password is hashed, 1000 is amir id, 1000 is the amir group id, /home/amir is its home path, /usr/bin/zsh is its shell path wich is zsh
```
#/etc/group ---> shows the groups and their informations such as their member and owner
```bash
$ sudo cat /etc/group
wheel:x:998:amir
amir:x:1000:
wireshark:x:150:amir
tor:x:43:
adbusers:x:964:
geoclue:x:963:
vboxusers:x:108:
dhcpcd:x:962:
#definition
 amir:x:1000: --> group name is amir, the id of group is 1000 and no one is a member of it, x is the password which not shown 
 
 whireshark:x:150:amir --> group name is whireshark, the id of group is 150, amir is a member of it, x is the password which not shown
```
----
## ***File's permission:***
```bash
$ ls -lrth
drwxr-xr-x 5 amir amir 4.0K Nov 10 12:42  Document
#definition
from left: - => type(d(directory),-(file)). --- ==> user, --- ==> group, --- ==> others
w(write), r(read), x(execute)
amir amir ==> amir(user) amir(group)
4.0K Nov 10 12:42 ==> its size and creation time
Document => file type
```
- #### tips:
	- in directory --> x(execute) mean you can open it like command #cd, w(write) --> you can write,delete,modify the files in a directory but you need execute permission too for midfying, r(read)  --> you can list the files of a directory

	- if the permission of a file was like this `drwxr-xr-x 5 amir amir`, the user amir which is create file can do anything with the file, the group of amir which any member of it, can read and execute onlty, and other only read and execute too, not modifying or writing.
---
## ***Modifying the permissions:***
- At first we must know the number of each permission:
	- x(execute) ---> 1
	- w(write) ----> 2
	- r(read) ---> 4
	- #so:
	- rw- ==> 6
	- r-x ==> 5
	- rwx ==> 7
	- -wx ==> 3
	- --- ==> 0
- to change the permission of files and directories we use #chmod which we learn it in commad section abow.
- to change the owner and group of files and directories use #chown 
- to change the group of files and directories use #chrgrp 
- to change your user main group and create files and directories with new group use #newgroup 
## ==***access mode***:==
- when you run `which passwd` it's a built-in command from `/usr/bin/passwd`:
**-rwsr-xr-x 1 root root 79K Oct 25 17:09 /usr/bin/passwd** ---> but what is the ==***S***==?
- as we learned about x(execute1),w(write2) and r(read4); we have something named #suid(s) which is a high executation mode means only the root and the owener(most be a sudoer) can execute them, also we have #guid for group --> ***so, #s stands for execute but only for owner and group if setted!***  
***In facts, suid control the running file permission, not user permission***
***So you cannot chage password directly in /etc/passwd but you can by passwd command!***
***because passwd bin file has S permission which when you run it, you execute the command by root permission not your own permission! ***
- octal of SUI ---> 4000 ---> u+s
- octal of GUID ---> 2000 --> g+s
- octal of sticky ---> 1000 ---> +t
***what is +t* ? +t as known sticky, when set nobody(except root) can remove or modify it except owner of file and root.***
