---
name: lpic
lesson: "26"
number: "26"
topic: customize and use shell environments
---
# Environment Variables:
#env ----> lists only main and permanent variables
#set ---> like env + list current variables too
`variable=value` ---> to set variable
#unset ----> to unset (remove) variable you made
#export ---> `export $variablename`
	imagine you have created a variable but, you wanna use it also in current shell on all tools and shell, cause variables only known in current variable and current mode not in other shell, service,....
#source ---> `source file` or `. file` or `source ./file.sh`
	imagine you have file, let say a .sh, also you have some variables there and you wanna use those variable in shell.
#alias ---> lists all aliases
	`alias aliasname='command'` ---> make an alias but it gonna be not useable in other program or shell.
#function ---> instead of alias, you can define a function to do more actions:
```bash
$amir-> learn() {
	ls
	echo "finish"
}
$amir-> learn
#Download Desktop file1
#finish
```

# Different shell environments
- ***Interactive shells***
	- login-shell ---> when you login by a terminal such as tty
	- run-shell ----> using shell but as login. it's such as using bash

- ***non-interactive shells***
	- when a service or tools need to run a shell, such as #ping or #bash or #redis-cli or ....

- ***interactive non-login*** ----> opening simple and not login shelll --> #zsh, #bash, #sh, #terminalapp

- ***/etc/skel*** ----> when a user logins, this files, runs:
```bash
$amir-> ls /etc/skel
#.  ..  .bash_logout  .bash_profile  .bashrc
```
	runs `bash_logout when user wanna logout`

***while booting, system runs first to last of these files in order, also if one them works well, it's not necessary to run all of them***
	1- /etc/profile                                                                                                       
	2- /etc/profile.d                                                                                                     
	3- /home/usernam/.bashprofile                                                                                         
	4- /home/username/.bash_login                                                                                         
	5- /home/username/.profile 
	