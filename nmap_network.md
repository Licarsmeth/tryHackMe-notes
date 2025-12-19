## Nmap
- **Multiple ways to specify targets**
	-   IP range using `-`: If you want to scan all the IP addresses from 192.168.0.1 to 192.168.0.10, you can write `192.168.0.1-10`
	-   IP subnet using `/`: If you want to scan a subnet, you can express it as `192.168.0.1/24`, and this would be equivalent to `192.168.0.0-255`
	-   Hostname: You can also specify your target by hostname, for example, `example.thm`
- **Host discovery**
	- nmap -sn `ip address(es)`
		- If our IP address is `192.168.66.89`,  we are scan the `192.168.66.0/24` network by `nmap -sn 192.168.66.0/24` command.
	- nmap -sL `ip address(es)`
		- This scan only lists the targets to scan without actually scanning them. For example, `nmap -sL 192.168.0.1/24` will list the 256 targets that will be scanned. This option helps confirm the targets before running the actual scan.
- **Port Scanning**
	- `-sT`
		- TCP connect scan – complete three-way handshake
	- `-sS`
		- TCP SYN – only first step of the three-way handshake, faster and stealthier
	- `-sU`
		- UDP scan
	- `-F`
		- Fast mode – scans the 100 most common ports
	- `-p[range]`
		- Specifies a range of port numbers – `-p-` scans all the ports
		- For example, `-p10-1024` scans from port 10 to port 1024, while `-p-25` will scan all the ports between 1 and 25.
		- 








<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNTk2MTE0NjIsLTE2NDMwNDg4NDksMT
MzNzA2NjMxOSwtMTUwNDI0NzI3MywyMDQzMzU2MDYwLC0xNTIz
MDUzNzUzLC0yMDg4NzQ2NjEyXX0=
-->