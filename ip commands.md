# Playing with IP in linux

- ***Send packet to other IP in your LAN***
	- **see own ip and interface**
		- ip addr show
		- shows current device ip
		- look for interface you use (e.g. `wlp0s20f3`) and the `inet` line like:
		- inet 192.168.10.5/24 brd 192.168.10.255 scope global wlp0s20f3
	- **see current neighbors**
		- ip neigh show
	-  **MAIN: find a target IP on the LAN**
		- arp-scan --interface=wlp0s20f3 --localnet
		- manually sends **ARP Request packets** to every IP in your subnet
		- It actively probes the LAN
	- **send packet**
		- ping -c 3 xxx.xxx.xx.xxx
		- -c means count
		- 3 means you send 3 icmp messages, then stop 
- ***Packet capture in your network (tcpdump)***
	



----------


<!--stackedit_data:
eyJoaXN0b3J5IjpbOTYzODA1MDUsNzkzNTQ5ODIzLDE3MjI3Mj
U0MDIsLTYwMjc3ODY5NiwxMTAyNTY3NjgxLC04OTI3ODM1Nzcs
LTE2NjA1MjQzNTAsLTEyNTcxOTEwODQsMjEyMjQ3MTQ2LDEwNj
k4NjYwNTAsMzg3MjA5MzFdfQ==
-->