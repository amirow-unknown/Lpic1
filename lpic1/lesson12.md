---
name: lpic
lesson: "12"
topic: shell, working on CLI
number: "12"
---
- There vary #SHELLs and #Terminal_emulator.
- #SHELL --> #bash , #zsh , #dash , #poweshell, ...
- #Terminal_emulator --> gnome-terminal . exfce-terminal , katty, alarcity, cmd, ...

how to know what's our #shell?
	echo $SHELL -> `prints the type of shell used in current shell`
	readlink /bin/sh -> `prints the linked file of /bin/sh with is a type of shell`
	ls -lrth /bin/sh -> `like readlink`
# commands:
- in linux. commands are in 3 categories:
	- builtin -> `command is built by shell`
	- links to a initialed bin file(executable) -> `there is executable file in /bin or /sbin or /usr/bin or /usr/sbin which, your command linked to that and when you run your command, actually you run that executable file.`
	- alias -> `in fact, aliases work like abbreviation, for define a alias and initial it by a command` -> 'alias where="pwd"'.
	how to know the commands type? by command #type 
	how to know the format of a file? by command #file
	how to know the link of a lined file? by #readlink or #ls 
- ##### example
```bash
echo $SHELL -> /usr/bin/zsh
ls -lrth /bin/sh -> lrwxrwxrwx 1 root root 4 Aug  1 23:26 /bin/sh -> bash
readlink /bin/sh -> bash

type cd -> cd is a shell builtin
type ls -> ls is an alias for ls --color=tty
type oblivion -> oblivion is /usr/bin/oblivion

file amir.txt -> amir.txt : ASCII text
file /bin/bash -> /bin/bash: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=d439d8c6534f7d0af736a4ece487e86bd49d7273, for GNU/Linux 4.4.0, stripped
```
# commands:
###### #cd: used for move different directories
- the 2 types of point to directory:
	- absolute path: /home/amir/Desktop/learning/main.go
	- relative path: Desktop/learning/main.go
		if in current path. the path which defined wasn't exist, you gonna get 'not found' error.
`~` -> this character is an alias to directory /home/user
`$HOME` -> this is a variable to directory /home/user
###### #pwd: shows the path of current directory
```bash
pwd -> /home/amir
```
###### #uname: shows information of your hardware and os
```bash
uname -s -> kernel name
uname -n -> hostname
uname -r -> the release of the kernel
uname -v -> version of the kernel
uname -m -> cpu architecture
uname -o -> os name
uname -a -> all information
uname -snrvmo ->Linux Amir 6.17.4-arch2-1 #1 SMP PREEMPT_DYNAMIC Sun, 19 Oct 2025 19:21:18 +0000 x86_64 GNU/Linux
uname -a -> Linux Amir 6.17.4-arch2-1 #1 SMP PREEMPT_DYNAMIC Sun, 19 Oct 2025 19:21:18 +0000 x86_64 GNU/Linux
```

# special characters:
- there some #special_character in shell, such as `/?\|[]{};:~$=*&<>'"`. for example `/` used for #path and #escape and #special_characters.
- `\a` -> alert
- `\b` -> backspace
- `\c` -> suppress trailing newline
- `\f` -> form feed
- `\n` -> new line
- `\r` -> carriage return
- `t` -> tab
- ==***Notice***== --> if you wanna use a special character in shell and get error, use / to escape it 

# Shell environment variables
- there are some shell variables which you can see them by command #env -> `echo $SHELL`
- Important Variables:
	#USER -> `echo $USER` -> amir
	#PATH -> `echo $PATH` -> `/home/amir/.config/nvm/versions/node/v24.7.0/bin:/home/amir/.cargo/bin:/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bin/core_perl:/var/lib/snapd/snap/bin`
	#EDITOR -> `vi`
	#HISTFILE -> `/home/amir/.zsh_history`
	#HOSTNAME or #HOST -> Amir
	#UID -> `1000` 
	#HOME -> `/home/amir`
	#PWD -> `/home/amir/Document/obsidian`
	#SHELL -> `/usr/bin/zsh`
###### some tips:
`$? -> shows the status code of previous command which 0 is sucessed`

#### setting #variable 
- *to define new variable ->* `name="amir"; echo $name -> amir`
- ==but==, you can only use it in current shell not any child process can access it, such as use it in a bash script to print it. you must use #export command .

- **how to set a variable as global?**-> you must set `export variable="value" in your` #zshrc or #bashrc and run `source bashrc/zshrc, now your variable is  ` #global.
#### important #variables
#PATH -> shows the paths of commands which when you a command, shell looks them by order to find your command and if it didn't you get error **~command not found~**    if you run `echo $PATH`: `/home/amir/.config/nvm/versions/node/v24.7.0/bin:/home/amir/.cargo/bin:/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bin/core_perl:/var/lib/snapd/snap/bin`
- there some paths which has seprated by `:` , it's exported in #/zshrc:
      `export PATH=$HOME/bin:$HOME/.local/bin:/usr/local/bin:$PATH`

### #commands 
- #which -> shows the path of executable format of command -> `which ping` ->*** /usr/bin/ping***
- #whereis -> shows the all files related to a command such as it's executable file, source, configs, manuall, etc. -> `whereis ping` -> ***ping: /usr/bin/ping /usr/share/man/man8/ping.8.gz***
- #whatis -> prints the command usage -> `whatis ping` -> ***ping (8) - send ICMP ECHO_REQUEST to network hosts***

# #history
- bash, zsh,... save their history in a path such as **/home/amir/.zsh_history**
- #history -> this command prints the history of user history commands.
- CTRL+r -> to search in history and then #TAB to select it and run it. or CTRL+O to run founded command.
- !! -> to run the previous command
- exit -> to exit of terminal
