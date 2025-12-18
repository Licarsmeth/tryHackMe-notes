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
	- **Basic commands**
		- `tcpdump -i INTERFACE`
			- Captures packets on a specific network interface
		- `tcpdump -w FILE`
			- Writes captured packets to a file
		- `tcpdump -r FILE`
			- Reads captured packets from a file
		- `tcpdump -c COUNT`
			- Captures a specific number of packets
		- `tcpdump -n`
			- Don’t resolve IP addresses
		- `tcpdump -nn`
			- Don’t resolve IP addresses and don’t resolve protocol numbers
		- `tcpdump -v`
			- Verbose display; verbosity can be increased with `-vv` and `-vvv`	
	- **Filtering**
		- By host
			- `host IP` or `host HOSTNAME`
			- `src host IP` for source host filtering
			- `dst host IP` for destination host filtering
		- By port
			- `port 53`
			- add src or dst for source or destination ports
		- By protocol
			- Simply add the protocol name, like `ip`, `ip6`, `udp`, `tcp`, and `icmp`
		- Logical operators
			- and, or, not
		- Advanced filtering
			- There are others like filtering by length (`greater length`), binary operations (`& ! |`, header bytes(`proto[expr:size]`), tcp flags(`tcp-syn`), etc. Visit [here](https://tryhackme.com/room/tcpdump) to know more
	- **Examples:**
		- `tcpdump -i eth0 -c 50 -v` captures and displays 50 packets by listening on the `eth0` interface, which is a wired Ethernet, and displays them verbosely.
		- `tcpdump -i wlo1 -w data.pcap` captures packets by listening on the `wlo1` interface (the WiFi interface) and writes the packets to `data.pcap`. It will continue till the user interrupts the capture by pressing CTRL-C.
		- `tcpdump -i eth0 host example.com and tcp port 443 -w https.pcap` will listen on `eth0`, the wired Ethernet interface and filter traffic exchanged with `example.com` that uses `tcp` and `port 443`. In other words, this command is filtering HTTPS traffic related to `example.com`



----------


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTcyMjcyNTQwMiwtNjAyNzc4Njk2LDExMD
I1Njc2ODEsLTg5Mjc4MzU3NywtMTY2MDUyNDM1MCwtMTI1NzE5
MTA4NCwyMTIyNDcxNDYsMTA2OTg2NjA1MCwzODcyMDkzMV19
-->