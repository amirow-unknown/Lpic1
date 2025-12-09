---
name: lpic
lesson: "34"
number: "34"
topic: Basic's of Network
---
### #TCP/IP --> transmission control protocol/ internet protocol
#### ***IP:***
- each device in the internet(internal or free), need an ip and port to connect to other clients or servers to communicate.
- there are 2 types of IP's --> ip4(255.255.255.255) or ip6(0000.0000.0000.0000.0000.0000.0000).
- now, ip v6 is growing cause ip v6s are letter than devices in the world --> ipv4 `2*32`  --> ipv6 `2*128` 
---
#### ip4:
- each number of ip4 is 1 octed(2*8) which each part can be 0-255 like 192.1.33.1
- there are 2 types of ip ---> private and public
	- private ips cannot be use in internet cause it used in internal networks
	- public ips sets by ISP and ISP gets from IANA.
- classes of public ip4:
	- A -----> 1-126(first octed) ==> 123.255.255.255
	- B ----> 128-191(first octed) ===> 143.255.255.255
	- C ----> 192-223(first octed) ===> 110.255.255.255
- classes of private ip4 
	- 192.168.255.255
	- 172.16.255.255
	- 10.255.255.255
---
# NAT:
- there are less ip4 than amount of devices which connect to internet.
- nat is a protocol which convert your private ip to public ip(not exactly!)
- when you get your internet from isp, and then you wanna connect to internet(external), isp gets your packets and sets it's own public ip4 on your packets and sent them to destination and when get's response, gives you. so lots of devices which needs to ip4, don't get ip4, in fact their packets exchange by a device which has ip4 and it knows how to handle the packets.
---
## subnetmask, network, broadcast, binary to decimal:
ip                     decimal              CIDR
10.0.0.0 ----> 255.0.0.0 ----> /8 
192.168.0.0 ---> 255.255.0.0 ---> 16
172.16.21.0 ---> 255.255.255.0 ---> /24
172.16.21.0 ---> 255.255.254.0 ---> /25 ---> the CIDR can be other number by changing the number of each octed.

ip                          netmask                    network                   broadcast
192.168.2.4 ---> 255.255.0.0/16 ---->  192.168.0.0 ------> 192.168.255.255
- example:
	- ip a ---> `docker 172.17.0.1/16`
	- 172.17.0.1/16 ----> 255.255.0.0/16 ----> 172.17.0.0 ---> 172.17.255.255
	- mean the ips that has number in ip 172.17.255.255, are in docker network!
	- note ---> first ip (172.17.0.1/16) is gotten by docker so the range is 172.17.255.254/16

- ***table of binary to decimal***
	-                     128     64   32   16    8    4   2   1 
	- 200--->        1         1     0       0     1   0   0    0  ----> 200=1100100
	- 255--->        1         1     1       1     1   1    1   1 ---> 255=11111111
--------
## TCP (transmission control protocol):
it's a reliable and trusted protcol which make sure your packets arrived and send in right order.
if a packet dropps, TCP knows and send it again until the downstream announce that the packet arrived. used more for services such as ssh, web content and any services whick all packets much be sent.
## UDP (user datagram protocol):
it's unreliable and untrusted protocol which doesn't make sure that your packet lost or arrived correctly.
if a packet dropps, UDP doesn't care and send next packets. used more for streaming services.

## ICMP (internet control messaging protocol):
ICMP used to network troubleshooting such as sending ICMP packets to server by command `ping` which sures connectivity(ICMP is not used for transferring data(not most of time:) ))

# Important Ports

| port number | service |
| ----------- | ------- |
| 22          | ssh     |
| 20,21       | ftp     |
| 23          | telnet  |
| 25          | smtp    |
| 53          | dns     |
| 80          | http    |
| 443         | https   |
| 110         | pop3    |
| 123         | NTP     |
| 139         | NetBios |
| 465         | smtps   |
| 995         | pop3s   |
### **tip** ---> file /etc/services which contains ports and their services list,
