## Unified Kill Chain 


- In (Initial Foothold)  
RWDEIC (all of cyber kill chain except Action on objective)
	- Reconnaissance - Target research via OSINT, social media scraping, network enumeration  
	- Weaponization - Bundle exploit with backdoor into deliverable payload  
	- Delivery - Phishing email, malicious USB, compromised watering hole website  
	- Social Engineering: Manipulating users to gain access.
	- Exploitation - Trigger vuln (buffer overflow, XSS) to gain code execution  
	- Persistence - Drop malware for persistence (rootkit, scheduled task)  
	- Defense Evasion: Avoiding detection by security measures.
	- Command and Control - Establish beacon to attacker's C2 server (HTTP, DNS tunneling)
	- Pivoting - Use compromised host as jumpbox to deeper network segments

- Through (Network Propagation)  
DPCLEP (D PC LEP, the pc left to p)
	- Discovery - Map internal network, AD enumeration, share discovery  
	- Privilege Escalation - Exploit kernel bugs, pass-the-hash, token impersonation  
	- Credential Access - Keylogging, LSASS dumping, SAM hive extraction  
	- Lateral Movement - RDP, SMBExec, psexec to other hosts  
	- Execution - Run payloads via WMI, PowerShell, scheduled tasks  
	

- Out (Actions on Objectives)  
CEI (See from ee, this eye, C E I)
	- Collection - Aggregate data to staging location (temp folders, registry)  
	- Exfiltration - Tunnel data out via DNS, HTTP POST, cloud sync  
	- Impact - Deploy ransomware, wipe data, destroy backups
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjkxMjA3MzUwLC05ODAxMzUzMTNdfQ==
-->