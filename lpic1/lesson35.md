---
name: lpic
lesson: "35"
number: "35"
topic: network in linux
---
- in linux and some other OS's, the NIC(network interface card) known as a interface you can connect to wireless internet or by lan. it's name todays is like "wlan0", "lo","eth0", .....
- *lo is a virtual network adapter which it point's to your device and 127.0.0.1. *

#### - the network configuration files are different based on your distro but in arch is like this:


----
# configuring your interfaces:
- #ifconfig -----> old but still uses
	- 
- #ip ----> net utility, use `ip switch help` to get help for each switch
	- addr ---> manage protocol address's
		- `ip addr` ---> shows all protocols and their config such as ip4,6, mtu, is it up or down, etc.
		- `ip -4/6 addr` ---> like above but shows ip version 4/6 only
		- `ip addr add ...` --> add new protocol
		- `ip addr change ...` ---> change a protocol config
		- `ip addr replace ...` ---> changing protocol address
		- `ip addr flush ` ---> flush protocol address
	- link ---> configure network devices
		- `ip link show wlan0` ---> shows wlan0 device info
		- `ip link set` ---> used to set changes:
		- `ip link set wlan0 up/down` --> set wlan0 up/down
	- maddr ---> managing multicast address's 
	- monitor ---> monitor state
	- route ----> manage routing table
		- `ip route` ---> shows routes
			- also you can see your default gateway
			- `ip route del redirected-ip` ----> deletes the routes which redirected-ip gets
			- `ip route add 8.8.8.8 via localhost` ---> if you send request to 8.8.8.8, it goes through localhost(doesn't get back response)
			- `ip route add default via 192.168.0.1` ---> setting 192.168.0.1 as default gateway.
			- `ip route add 8.8.8.8 via ip 172.17.0.1 dev docker0` ---> adding interface too
	- mrout ----> managing multicast routing
	- rule ---> manage routing policy 
	- tunnel ---> configuring tunnels
	- neight ---> manage neighour and arp table
		- `ip neight` ---> shows macaddress and 
	- addrlabel ---> manage addrlabel
	- **Notice**---> use -4 for ip4 and -6 for ip6
#ping ---> send icmp packets(we all know about this :/)
	`-c` ---> count of sending request
	`i` ---> delay between each request(second)
		you can attack by this switch(yah yah :) ) --> `ping -i 00000000000000.1`
	`s` ---> size of packets
	`-4` ---> ip4
	`-6` ---> ip6

----
- #### Network manager 
- todays, you don't need to configure your NIC and other stuff such as getting ip from DHCP or connecting to wifi manually or setting dns or ....
- **NetworkManager** is a newer service which does all of this that cause you can connect to wifi by one click(gui) or your dns ip and .... sets automatically. you can see it's status by command **`sudo systemctl status NetworkManager`** , also it's configuration file is on **/etc/NetworkManager**

#nmcli ---> tools of CLI which you can access to your wifi.

---
- computers know ip address's but we know names better, like localhost for 127.0.0.1, if you send request to localhost, in fact, you're sending the request to 127.0.0.1 ---> `ping localhost`. this is used in dns resolution too ---> `ping google.com` ----> `ping 216.239.38.120`
- ***/etc/hostname*** ----> contains your hostname 
- ***/etc/hosts*** ----> contains hostnames
	- if you add `127.0.0.1 google.com` and search for `google.com` in browser, you redirect to localhost!
- ***nsswitch.conf*** ---> contains the order of getting a value of your information, such as password or *hosts*
	- 
#hostname ---> shows and setting your system hostname
```bash
$amir-> hostname #-> amir
$amir-> hostname -F filenamecontainshostname #-> newhostname
$amir-> hostname -a #shows aliases
$amir-> hostname -d #shows dns domain name
```
#hostnamectl ---> controling your system hostname.
```bash
$amir-> hostnamectl #shows user information such as hostname, icon name, chassis, location, machine and uid, kernel, architecture, 
$amir-> hostnamectl set-hostname hostname #sets static/permanent hostname
```
- there are 2 type of hostnames: **static(permanent)** or **transient(temporary)**, ***to set transient hostname, you must remove static hostname*** 
```bash
$amir-> sudo hostnamectl --static/transient#shows static/transient hostname
$amir-> sudo hostnamectl --static hostname "amir"#setting amir as static hostname
$amir-> sudo hostnamectl --static hostname "" #removing static hostname
$amir-> sudo hostnamectl --pretty hostname "amir"#setting pretty hostname
```
- **extra options**
```bash
$amir-> hostnamectl location#shows location value
$amir-> hostnamectl hostname#shows hostname value
$amir-> hostnamectl chassis#shows chassis value
$amir-> hostnamectl icon-name#shows icone-name value 
```
***pretty---->*** it's a type of hostname which used to describe your system and your information. also file ***/etc/machine-info*** contains your pretty hostname.
```bash
$amir-> sudo hostnamectl --pretty hostname "it's amirreza's system"
```
***chassic--->*** it's determines the type of your device, such as laptop, desktop, embedded, tablet, watch, server, vm,... .
```bash 
$amir-> sudo hostnamectl Chassis "your choice"
```
------
- # DNS: Domain name system
- if i want to explain it, i must spend several days to write down :)        but in simple language:
- imagine dns is like your contacts and their phone number, **you don't remember their numbers, you know their name which you saved!**
- when you send request to google.com, based on your **host order in /etc/nsswitch.conf** file, you send dns query to get google ip(or a group of ip's and other stuff such as NS and), then you send request to it's ip address not it's domain name(google.com).
- DNS address file in linux is ***/etc/resolv.conf*** which contains DNS ip address to send dns queries and get response to it.
- ###### notice ---> as we said, systemd and it's daemon are sorrounding all the process, so there is or are services which handle your network such as #networkmanager and it's daemon #systemd-resolved.conf, so if you set other DNS ip, it get's to default value which networkmanager sets! :(((
---
# nsswitch.conf
```bash
# Name Service Switch configuration file.
# See nsswitch.conf(5) for details.
passwd: files systemd #to get useringo use systemd file
group: files [SUCCESS=merge] systemd#to get groups info use systemd file
shadow: files systemd # to get password use shadow file
gshadow: files systemd

publickey: files

hosts: mymachines resolve [!UNAVAIL=return] files myhostname dns  #to network process, first look to mymachone, files, myhostname file and then dns
#so any resolving request, process by mymachines, then myhostname and then dns
networks: files

protocols: files
services: files
ethers: files
rpc: files

netgroup: files
```
---
#traceroute ---> shows the packets goes through nodes(routers, servers, isp, modem, ....) to destination.
#tracepth ---> like #traceroute but shows names of nodes and MTU(except no replys)

---
#dig #nslookup ----> ***both used to dns resolution***
`dig A google.com` ---> record A(ip4)
`dig AAAA google.com` ---> record AAAA(ip6)
`dig NS google.com` ---> nameservers
and .... ----> `dig RECORD domainname`
`+short` ----> only output

---
#netstat --->  `Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships`
###### *switches:*
	`-a` ---> shows all tcp&udp connections and all listening ports
	`-t` ---> tcp connections
	`-u` ---> udp connections 
	-l --> shows all sockets which are listening for incoming connectiosn
	-p ---> shows all PIDs for each connection
	-n --> shows ips and ports in numeric format not resolving names
	--numeric-hosts ---> shows host ips in numeric format
	-r --> routing table
	-s ---> statics for protocols
	-c ---> following option
	-e ---> extended, usernames and timers
	-x ---> unix connections
	-i ---> monitoring network interfaces --> netstat -ie / watch -n 1 netstat -i
	-g ---> shows group memberships
	-h ---> like other tools and commands for help
---
#ss ---> `network utility to investigate sockets(newer than netstat)`
	-a ---> all connections
	-l ---> listening socket connections
	-t ---> tcp connections
	-p ---> pid
	filternings: ----> ss -tap state listening---> shows all tcp connections which all in established state
		listening 
		established