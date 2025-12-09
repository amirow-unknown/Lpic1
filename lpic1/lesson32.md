---
name: lpic
topic: system logging
lesson: "32"
number: "32"
---
- **what's the logging and why and how?!**
	one of the reason to use linux, is it's logs. each service and programe even boot process saves in seprated file to troubleshoot them.
- ***what utility manages logs?*** ---> first utility name was #syslog and then #syslog-ng, and now it's #rsyslog. but do we now use only #rsyslog? the systemd is conquering all parts of linux, and logging manage is include too. systemd service has a service called #journald which manages log and has command named #journalctl.

- ###### #rsyslog ----> log manager service
- it get all logs as message from different programs and save them in seprate file or directory(for huge sizes), their format is **plain text** which cause to use them and do actions on them such as regex and find your solutions.

- ###### #logrotation ---> a tool to manage log files
- Imagine, after .... years later, you gonna have a lots of log files which are getting full your disk.**what to do?** 
- #logrotation is a tool which which manages log files, like **after how many times delete old log files?**, **each service must have how many log files?**, **and so on....** :
- command logrotate --> manage logs and debug and ....
- directory --> **/etc/logrotate.d** ---> contains configuration files of service to manage their logs.
- ***/etc/logrotate.d/httpd :***
```bash
root@debian:# cat /etc/logrotate.d/httpd
/var/log/httpd/term.log {
  rotate 12
  monthly
  compress
  missingok
  notifempty
}

/var/log/httpd/history.log {
  rotate 12
  monthly
  compress
  missingok
  notifempty
}
```
- file --> /etc/logrotate.conf ---> configuration file for logrotate manage:
```bash
root@debian:# cat /etc/logrotate.conf
# see "man logrotate" for details

# global options do not affect preceding include directives

# rotate log files weekly
weekly

# keep 4 weeks worth of backlogs
rotate 4

# create new (empty) log files after rotating old ones
create

# use date as a suffix of the rotated file
#dateext

# uncomment this if you want your log files compressed
#compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

# system-specific logs may also be configured here.
```
***log rotate config table:***
```bash
weekly ---> rotate logs weekly
missingok --> is it ok that there is no log for this week
rotate NUM ---> only have NUM log files and remove older files
compress ---> compress log files
create NUM USER GROUP ---> create file by this permission and user and group
pre & post rotate ---> run command or script before and after rotate
```
***tip***---> `log rotate runs on cron in /etc/cron.daily and based on daily jobs`
- more and details in ![[logrotation]]
# boot process log --->
kernel logs boot process before knowing partitions and disk and write them in ram at kernel ring buffer and you can access them by command #dmesg

# *famous log files:*
- log files and some of their directory save in #/var/log
- #/var/log/auth.log ----> saves all login logs
- #/syslog ---> most of logs which #rsyslog gets which doesn't specify path for log.
- #/kern.log ---> kernel messages log
- #/message --> informative messages from services
- #/utmp or #/wtmp ---> successful logins
- #/btmp ---> failed logins
- #/faillog --> failed logins
- #/lastlog ---> date and time of recent user logins
# *service logs:*
- service logs create files or directories which can be modifyed in the passing time, such as #/var/log/apache2 or #/var/log/tor.log or ....

# *Rsyslog*: [[rsyslog]]

# *journald and journalctl:* [[journald]]
