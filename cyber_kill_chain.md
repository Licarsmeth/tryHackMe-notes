## Cyber Kill Chain

7 Phases (Lockheed Martin model):
RWDEICA
(Ready to Win? Don't Engage In Combat Attack)

1.  Reconnaissance - Target research (OSINT, employee names, tech stack)
	- Type- active recon, passive recon
	- Eg: Email harvesting
	- Tools: Hunter.io, OSINT Framework
    
2.  Weaponization - Create malware payload (exploit + backdoor)
    
3.  Delivery - Transmit payload (phishing email, USB, watering hole)
	- 

5.  Exploitation - Trigger vulnerability (buffer overflow, XSS)
    
6.  Installation - Drop persistence (backdoor, rootkit)
    
7.  Command and Control - Phone home to C2 server (beacons, DNS tunneling)
    
8.  Actions on Objectives - Exfil data, ransomware, lateral movement
    

Break chain at any phase stops attack  
Recon block = Nmap/IDS signatures  
C2 kill = network segmentation
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NTY0NTI1NjksLTE1OTQyMDA5MjYsND
QyODUxNTIyXX0=
-->