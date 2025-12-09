---
name: lpic
topic: rsyslog
---
- #rsyslog is new generation of #syslogng and get's logs from vary facilities and make thier log file based on rules and it's config file. it's config file is **/etc/rsyslog.conf** and subconfig files is **/etc/rsyslog.d**.
- #rsyslog config file has 3 main parts ---> **Modules**, **Global Directives**, **Rules**
###### *Module* ---> requirement module for it's logging process, such as UDP module.
###### Global Directives ---> to create files and directories for what permission and group and user and umask
###### Rules ---> setting rules for rsyslog service to how get logs and log them in which files, priority, facilities, and ..... !
---
- cat **/etc/rsyslog.conf**
```bash
#module
module(load="imuxsock") # provides support for local system logging
module(load="imklog")   # provides kernel logging support
#directives
$FileOwner root
$FileGroup adm
$FileCreateMode 0653
$Umask 0022
#include all sub-rsyslog-config files
$includeConfig /etc/rsyslog.d/*.conf
#
#RULES
cron.*    /var/log/cron.log #all priority of cron facility written in cron.log
kern.*    /var/log/kern.log #all priority of kernel facility written in kern.log
mail.*    /var/log/mail.log #all priority of mail facility written in mail.log
user.*    /var/log/message.log #all priority of user facility written in user.log
*.emerg   :omusrmsg:* #all emergency priority any facility written in omusrmsg.log

*.crit;mail.non   /var/log/crit.log ##all facilities of critical priority written in cron.log except mail facility
```
##### - facility (who sends log to log manager):
	kern, user, mail, cron, daemon, shell, security, console, syslog, auth,..
##### - Priority (levels of log messages):
	emerg/panic, alert, crit, err/error, warn/warning, notice, info or debug
##### - Actions (what to do on log messages):
	filename ---> /path/path/*.log
	user ----> amir ==> (notify in user screen)
	@ip ---> @172.22.3.31 ==> (send log to a log server and there, the log             manager do actions based on it's config)
---
# **==Notice:==**
- when you determine priority like this:`cron.notice /var/log/cron.log`, cause before notice, there are *`warn, error, crit, alert, emerg`* priorities, these logs save in /var/log/cron.log file too.
- To fix this issue, you can specify only one specific Priority like this --> *`shell.=err /var/log/errsheell.log`*
# **==Tip:==** 
- what if your log utility and service crash and you need to see kernel logs?
- klogd is a daemon which logs kernel crache's!
---
# commands:
#logger ----> sending log message 
- `logger "amirreza"`
- `logger shell.alert "amirrezaisin denger"`
#lastlog ---> shows recet logs ---> -u used to specify username
#faillog ---> used to print failed attemps to login 
