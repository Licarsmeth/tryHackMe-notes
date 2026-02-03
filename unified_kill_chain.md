## Unified Kill Chain 


- In (Initial Foothold)  
9: RWDSEPDCP ( just add SuDiP, SDP, Social eng, Def ev, Piv, to cyber kill chain's RWDEICA. also remove the last Action, oh and installation is now persistence. Doesn't make much sense ik, but it does for me hehe)
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
5: DPECL (di pee, ee see, L) (again, makes sense to me wkwk)
	- Discovery - Map internal network, AD enumeration, share discovery  
	- Privilege Escalation - Exploit kernel bugs, pass-the-hash, token impersonation  
	- Execution - Run payloads via WMI, PowerShell, scheduled tasks
	- Credential Access - Keylogging, LSASS dumping, SAM hive extraction  
	- Lateral Movement - RDP, SMBExec, psexec to other hosts 

	
- Out (Actions on Objectives)  
4: CEIO (old mcdonald's had a farm, CIEIO)
	- Collection - Aggregate data to staging location (temp folders, registry)  
	- Exfiltration - Tunnel data out via DNS, HTTP POST, cloud sync  
	- Impact - Deploy ransomware, wipe data, destroy backups
	- Objectives: Achieving the final, overarching goal of the attack
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY3MTYxMTYwMCwxNDIxNTYxMzQ3LC05OD
AxMzUzMTNdfQ==
-->