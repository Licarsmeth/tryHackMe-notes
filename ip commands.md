# Playing with IP in linux

- ***Send packet to other IP in your LAN***
	- **see own ip and interface**
		- ip addr show
		- shows current device ip
		- look for interface you use (e.g. `wlp0s20f3`) and the `inet` line like:
		- inet 192.168.10.5/24 brd 192.168.10.255 scope global wlp0s20f3
	- **see current neighbors**
		- ip neigh show
		- shows hosts you've already talked to, not every neighbors
	-  **MAIN: find a target IP on the LAN**
		- arp-scan --interface=wlp0s20f3 --localnet
		- manually sends **ARP Request packets** to every IP in your subnet
		- It actively probes the LAN
	- **send packet**
		- ping -c 3 xxx.xxx.xx.xxx
		- -c means count
		- 3 means you send 3 icmp messages, then stop 



----------


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc0NTg5NTc2NCwxMzI1ODQ0NzM4LDc5Mz
U0OTgyMywxNzIyNzI1NDAyLC02MDI3Nzg2OTYsMTEwMjU2NzY4
MSwtODkyNzgzNTc3LC0xNjYwNTI0MzUwLC0xMjU3MTkxMDg0LD
IxMjI0NzE0NiwxMDY5ODY2MDUwLDM4NzIwOTMxXX0=
-->