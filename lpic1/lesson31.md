---
name: lpic
topic: localization and internationalization and maintaining timezone
lesson: "31"
number: "31"
---
- ***how linux and systems know the times!***
	- each laptop and pc have a clock in hardware which knows time.
	- you can see it or modify it by `hwclock` command.
	- when you turn on your pc, the linux time service asks hwclock to know the time, which means if you modify hwclock, your time zone gonna be change too.
	- but to know exact timezone there are #ntp and #chrony protocols.
		- #ntp has a service named #ntpd which sends request to **pool.ntp.org** to get correct time. also the chrony does something like this.
	- you can modify #hwclock by `sudo hwclock --localhost --set --date="..."` or change it to default by `sudo hwclock -u -w`
###### #TimeZone:
- do you know how to change your timezone in linux?
```bash
#setting time by timedatectl
timedatectl ---> shows you timezone and UTC information
timedatectl list-timezones ---> list avaible timezones
timedatectl set-timezone yourcity ---> set timezone
------------------
#setting time by linking your timezone to localtime file
ls /usr/share/zoneinfo #find your city
sudo unlink /etc/localtime #unlink from previous timezone
sudo link -s /etc/zoneinfo/Asia/Tehran /etc/localtime #set tehran to timezone
---------------
#you can see what's your timesone in :
/etc/timezone
``` 
- also there are some tool such as #date and #cal 
#date ---> time and date
```bash
date ----> Sun Nov 30 11:34:25 AM +0330 2025
date +'%Y' ---> 2025
	%Y -> year
	%m -> month
	%d -> day
	%H -> hour
	%M -> minutes
touch `date +'%Y_%m_%H_%m'.sh` ---> 2025_Nov_11_15.sh
```
#cal ---> calender
```bash
cal year ---> shows that year calender
```
###### #language_configuration 
```bash
locale ----> shows your language configuration like this
➜  ~ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
----
also you can change your language format in /etc/locale.conf
cat /etc/locale/conf
---> LANG=en_US.UTF-8

```