---
name: lpic
lesson: "25"
number: "25"
topic: find files and place them in correct location
---
FHS ---> Filesystem Hierarchy Standard
```bash
bin ---> binary files
boot ---> booting files and configs
dev ---> devices and blocks
etc ---> settings and configurations
home ---> home of user
lib ---> share libraries
lib64 ----> share 64bit libraries
mnt ----> temporary mount file
opt ----> add-on applications packages
proc ---> process
root ---> root home
run ----> removeable medias
sbin ----> system binary files
snap ----> snap
srv ---> data serves for server 
sys ---> kernel and hardware configuration
tmp ---> temporary files which deletes after boot
usr ---> secondary hierarchy
var ----> variable files such as log files
```
- when you run a command, how the shell know to find that command executable file? ----> ***$PATH***
```bash
$amir-> echo $PATH
/home/amir/.config/nvm/versions/node/v24.7.0/bin:/home/amir/.cargo/bin:/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/bin/site_perl:/usr/bin/vendor_perl:/usr/bin/core_perl:/var/lib/snapd/snap/bin
#from left to write, each path has more priority and shell looks in order from left to right!
```
#which ---> finds first path in $PATH that contains given command!
```bash
$amir-> which ping
/usr/bin
#-a ===> all paths which has your command
$amir-> which -a ping
/usr/bin
/bin
```
#where ---> looks to all paths in $PATH and selects the paths contains given command
```bash
$amir-> where ping
/bin
/usr/bin
```
#whereis ---> find first path of command ping and also it's man(manual) file
```bash
$amir-> whereis ping
ping: /usr/bin /usr/share/man/man8/ping.8.gz
```
#whatis ---> print what does command do.
```bash
$amir-> whatis echo
#echo -display a line of text
```
#tfile ----> prints the type of files and directories
#type --> prints the type of command->built-in or not
#find ---> let's learn some more tricks
```bash
-user ---> specify user of files
-group ---> specify the group of files
! -user ----> files created by any user but ....
! -group ---> files created by any group but ... 
```
#### #locate
- locate command has another command which is updatedb!
- updatedb updates it's database at each specific time of list of files and directories and their path,
- when you run locate or plocate, it looks at database and looks for your given word to find it's paths.
#updatedb ---> also you can update it's database manually by this command.
```bash
#imagine you make a file right now and updatedb database is not track it yet.
$amir-> touch amir
$amir-> locate amir
#nothing
$amir-> sudo updatedb
$amir-> locate amir
#/home/amir/Desktop/amir
```
