#### different between su and sudo! command su and sudo!
#su used to change your user
#sudo to run command as root
##### sudo command:
- -b ---> runs command in background
- -p ---> customize prompt to ask password(not important://)
- -k ---> asks password for next time (ignores user's timestamp)
- -u ---> runs sudo command but as other user ---> `sudo -u amir touch /etc/mamaly`
- -g ---> like -u but for group
	- sudo -u mamaly -g wheel touch newfile ----> files owner is mamaly and group wheel
- -s ---> runs the shell specified by the SHELL environment variable if it is set or the shell as specified in the file passwd.
- -l ---> shows the commands allowed (and forbidden) the user on the current host.
##### su command:
- -m --> It preserves the original user's current environment variables(you doesn't lose your pretty configurations in root mode)
- -s ----> runs specific shell after login ---> `su root -s /bin/zsh`
- -f ---> doesn't review shell configure and user variables, usefull for single command
- --session-command=`command` ---> runs command but as user to login but doesn't create new session

## ***sudoer***
***Note ---> use command #visudo to modify sudoers file.***
- if you create a user, he can't to access to run sudo, to run command as root privilege, so it must determines in sudoers file that the user is in sudo group.
- there are 2 type of users in linux
	- 1---> users who have not permission to run high-permission commands by using sudo to run as root privileges.
	- 2---> users who have permission to run high-permission commands by using sudo to run as root privileges
- your user must be set in #/etc/sudoers file to have access to run sudo command.
- also you can add your user to root group --> `sudo usermod -aG root mamaly`
- *file /etc/sudoers is contains lines like this:*
- ```bash
## User privilege specification
root ALL=(ALL:ALL) ALL#user root, all hosts(currenlty, this machine), as all user and all group, can runs all command 
amir ALL=(ALL) ALL# user amir, all hosts(currenlty, this machine), as all user, can runs all command
%wheel ALL=(ALL:ALL) ALL#% indicates group(it's users) not user, all hosts(currenlty, this machine), as all users and groups, can run all command 
```

##### why command #sudo needs user password but #su_root needs root's password?
- when you run #sudo, you're user most have sudoer permission to run sudo command, so if you had, you only need to enter your own pass.
- but when you use #su_root or #su_- you're loginning in root user and need it's environment variables, so it needs root password.

# ==commands:==
#w ---> lists logged-in users and some information about them.
#who ---> shows which users has logged-in
#last ---> shows more information of logins and  logouts 
#passwd ---> we learned this command but switch -S is good to know(shows the status of current user)
	`mamaly P 2025-07-10 0 99999 7 -1` 
#chage ---> gives information of user's password status
	`chage -l amir`

# suid & guid & sticky

- in simple introduction, if suid has set, the other users can execute it by the owner of the file permission. ex:
	- the executable file of passwd or any executable files which need to run as root or specific user, can set suid which other users can run it too(as owner of file permission)
	`chmod u+s`
- guid is like suid but for permission of file group.
	`chmod g+s`
- if a file has sticky permission, means no one unless root user can remove or rename it
	`chmod +t`


### manage resources for different users
- you can change and manage the resource usage for each user by command #ulimit.
```bash
-t: cpu time (seconds)              unlimited
-f: file size (blocks)              unlimited
-d: data seg size (kbytes)          unlimited
-s: stack size (kbytes)             8192
-c: core file size (blocks)         unlimited
-m: resident set size (kbytes)      unlimited
-u: processes                       30480
-n: file descriptors                1024
-l: locked-in-memory size (kbytes)  8192
-v: address space (kbytes)          unlimited
-x: file locks                      unlimited
-i: pending signals                 30480
-q: bytes in POSIX msg queues       819200
-e: max nice                        0
-r: max rt priority                 0
-N 15: rt cpu time (microseconds)   unlimited
```
- so you can set limit by switches which mentioned, for example by switch ***-t*** you can set cpu usage time for user, for example each process which it's pid is for that user, will kill after specific time.
- ##### notice: it's temporary and for current shell, file /etc/security/limits.conf is permanently.