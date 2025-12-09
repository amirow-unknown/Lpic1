---
name: lpic
lesson: "16"
topic: process in linux and managing them
number: "16"
---
- each service or command which you run on your linux, has pid which you can manage it.
- in windows and graphical desktop you can run some and even numbers of process together, but in shell if you run 1 process and it continoues to run it, you must kill or run it in background. also you can use #tmux!
- you can use ***ctrl+z*** to stop your process and send it to background and run it again by command ***fg***,
- #jobs --> to see all stopped or in background process
- #fg ---> to keep the process runnig and not in background.
- #bg ---> to move your stopped process to running in background.
- #bg & ---> to suspend your process and keep it in background
#PID and #PPID
```
   PID TTY          TIME CMD
   6633 pts/1    00:00:01 zsh
   9692 pts/1    00:00:00 ping
   9720 pts/1    00:00:00 ps

```
	the 9692 is the PID of service ping
	the 6633 is the PPID which is shell that ran the the command zsh
- also you can use & to suspend and send your command to background.
- if the a PPID terminates, it's PIDs gonna terminate too. to solve this error, use #nohup command.
- `nohup ping google.com` --> if you terminate the terminal, ping gonna runs and not terminate.
- `nohup ping google.com &` --> send the process to background too.
- #kill -> to kill the PIDs
	- kill -9 PID ---> kill the process with no mrcy.
	- kill 1 PID ---> anounce to the PID that it's PPID is terminated and it must terminate too unless it ran by nohup.
	- killall NAME ---> kills all the process with entered name
- also #pkill
	like #killall but you just enter a peace of process name and it terminate all process which has that name

---
# Monitoring process:
```commands
ps
ps -e
ps -f
ps -ef
pgre
top
free
uptime
watch -n

```
#ps ---> shows the process and their #PID in current shell not golabally.
#ps -e ---> like #ps but globally, like other service #PIDs
#ps -ef ---> `-f` shows full format and `ps -ef` shows the all process in full format.!
#pgrep{name} ---> shows the PID of the INPUT name such as `pgrep tor`
#watch ---> to run a command periodically, like `watch date` to run #date command each 2s.
#watch -n --> `watch -n1` ----> to determine the time reload for watch.
#uptime ---> shows the uptime and load average
#free -h -> shows the memory and swap usage.
#top ---> ***monitoring the PROCESS in LINUX!***
	*shift + m* --> sort the process by memory usage 
	*shift + p* ---> sort .................. by cpu usage
	/ ----> to search for a process
	top -p PID ---> top the PID
	top -p `pgrep ssh` top for the PID of ssh
	
#btop ---> pretty version of #top.

## #tmux:

#tmux --> to go in tmux mode!
	#ctrl+ b then % ---> to half the page in vertical mode.
	#ctrl + b then " ---> like `ctrl+b then %` but in horizontal mode.
	#ctrl + b then d ---> to detach
	#tmux ls ---> lists the tmux sessions
	#tmux attach -t `numberofsession` ---> to go in session mode
	#ctrl + b then c ---> to create new window
	#ctrl+b then numberofpage ---> to go to the suppose page
	#ctrl + b then `pagedown` or `pageup` or `pageleft` or `pageright` ---> move between tabs
	#ctrl + b + t ----> time in tmux
