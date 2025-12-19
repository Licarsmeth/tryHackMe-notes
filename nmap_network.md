## Nmap
- **Multiple ways to specify targets**
	-   IP range using `-`: If you want to scan all the IP addresses from 192.168.0.1 to 192.168.0.10, you can write `192.168.0.1-10`
	-   IP subnet using `/`: If you want to scan a subnet, you can express it as `192.168.0.1/24`, and this would be equivalent to `192.168.0.0-255`
	-   Hostname: You can also specify your target by hostname, for example, `example.thm`
- **Ping scan (local or remote scanning)**
	- nmap -sn `network address`
		- If our IP address is `192.168.66.89`,  we are scan the `192.168.66.0/24` network by `nmap -sn 192.168.66.0/24` command.
	- nmap -sL `network address`
		- 







<!--stackedit_data:
eyJoaXN0b3J5IjpbMTIxMjgyNzAwNSwtMTUyMzA1Mzc1MywtMj
A4ODc0NjYxMl19
-->