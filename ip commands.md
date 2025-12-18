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
- ***Packet capture in your network***
	- `tcpdump -i INTERFACE`
		- Captures packets on a specific network interface
	- `tcpdump -w FILE`
		- Writes captured packets to a file
	- `tcpdump -r FILE`
		- Reads captured packets from a file
	- `tcpdump -c COUNT`

Captures a specific number of packets

`tcpdump -n`

Don’t resolve IP addresses

`tcpdump -nn`

Don’t resolve IP addresses and don’t resolve protocol numbers

`tcpdump -v`

Verbose display; verbosity can be increased with `-vv` and `-vvv`


----------


<!--stackedit_data:
eyJoaXN0b3J5IjpbMzE2Nzk0NjAyLC0xMjU3MTkxMDg0LDIxMj
I0NzE0NiwxMDY5ODY2MDUwLDM4NzIwOTMxXX0=
-->