---
name: lpic
lesson: "17"
topic: modifyinh process execution priority
number: "17"
---
### what's the nice-ness?
- in linux, each process, has a number between `-20 to 19` which determine the priority for cpu to work on impotant process and high priority.
  - cpu gives it's power and time to less NICE numbers such as `-20` which is the most nice level and high priority for cpu.
  - so if cpu must compute between 2 process which the nice number of one of them is 19 and another one is -20, so cpu compute the process with nice number -20 first.
  - number 0 is mid-level and not important and not invaluable.
- ***you can see the nice-ness of your process in #top command***
#nice_0 --> by default most of process runs by nice_ness 0,  which determine to run it normally.
#nice_-20 --> so fast
#nice_19 --> chill man, it's runing
# command 
#nice --> to run a command and determine the nice-ness of it 
- `ping google.com` ---> this works alone and default nice-ness which is 0
- `nice ping google.com` ---> which works alone and nice-ness 10.
- `nice -n number command` ---> to run a command and determine nice-ness number.
- ***pay attention--> for mines number of nice command which are important, you need to be root. unless you get this error and your command runs in normal level not your wanted level: ***
	`nice -n -20 ls` --> `nice: cannot set niceness: Permission denied`
	`desktop downloads amir pictures`
- *why you must use nice and high priority numbers?* ==> imagine, you must update, backup, run a command, etc. so you're in hurry, use nice and high priority numbers to increase your process speed.
#top --> to see all process information which one them is #nice number.
#ps -l ---> list the top information but for process in it's shell
#renice --> to change the nice number of process 
	`sudo renice PID -n -12` 
	you must use the PID of your process to change it's ncie-ness number
