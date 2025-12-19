## Nmap

Use with sudo when you can. You get a minimal portion of Nmap’s power when running it as a local user. For instance, Nmap would automatically use SYN scan (`-sS`) if you are running it with `sudo` privileges and will default to connect scan (`-sT`) if run as a local user. The reason is that crafting certain packets, such as sending a TCP SYN packet, requires root privileges.

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
	- `-sT`: TCP connect scan – complete three-way handshake
	- `-sS`: TCP SYN – only first step of the three-way handshake, faster and stealthier
	- `-sU`: UDP scan
	- `-F`: Fast mode – scans the 100 most common ports, unlike the 1000 common ones by default
	- `-p[range]`:  Specifies a range of port numbers – `-p-` scans all the ports
		- For example, `-p10-1024` scans from port 10 to port 1024, while `-p-25` will scan all the ports between 1 and 25.
- **Extracting more information**
	- Use with the other options. Like `nmap -sS -O ip`
	- `-O`- OS detection, but not always reliable or accurate. Close estimation
	- `-sV`- Service and version detection
	- `-A`- OS detection, version detection, traceroute, and other additions
	- `-Pn`- Scan hosts that appear to be down as well forcefully
- **Controlling the timing**
	- `-T<0-5>`: Timing template 
		- – paranoid (0), sneaky (1), polite (2), normal (3), aggressive (4), and insane (5)
		- For example, you can add `-T0` (or `-T 0`) or `-T paranoid` to opt for the slowest timing.
	- `--min-parallelism <numprobes>` and `--max-parallelism <numprobes>`
		-  Minimum and maximum number of parallel probes
		- Parallel probes in Nmap means sending multiple scan probes simultaneously to different hosts/ports instead of sequentially (one-by-one).
		- use lower max for more stealth, higher min to do everything quicker.
	- `--min-rate <number>` and `--max-rate <number>`: Minimum and maximum rate (packets/second)
	- `--host-timeout`: Maximum amount of time to wait for a target host
- **Controlling the output**
	- -v for verbose. 
		- vv or even vvvv or v4 can be used to increase verbosity. 
		- can be added while nmap is scanning, by simply typing v
	- -d for debugging level output 
		- even more info than -v. 
		- can also be increased upto -d9, which is a lot
	- Saving scan report
		-  `-oN <filename>` - Normal output
		-   `-oX <filename>` - XML output. Used in tools like metasploit.
		-  `-oG <filename>` - `grep`-able output (useful for `grep` and `awk`). Better for machine parsing and automation
		- `-oA <basename>` - Output in all major formats








<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMzU5Mzc3MDYsNjg5NTk2MzI5LC0xND
c2MDA2MDc0LC02Mjg3NTk1LDE1MzE2NTU0NSwtMTY4NDQ0MTk1
NywtNDI0MDI3NTM3LC0xNjQzMDQ4ODQ5LDEzMzcwNjYzMTksLT
E1MDQyNDcyNzMsMjA0MzM1NjA2MCwtMTUyMzA1Mzc1MywtMjA4
ODc0NjYxMl19
-->