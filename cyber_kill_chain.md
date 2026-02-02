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
	- Watering hole attacks are targeted and designed to aim at a specific group of people by compromising the website they are usually visiting, redirecting them to a malicious website of the attacker's choice or creation

5.  Exploitation - Trigger vulnerability (buffer overflow, XSS, zero-day)
    
6.  Installation - Drop persistence (backdoor, rootkit, and a LOT more things, like timestomping can also be done here)
    
7.  Command and Control - Phone home to C2 server (beacons, DNS tunneling)
    
8.  Actions on Objectives - Exfil data, ransomware, lateral movement
    

Break chain at any phase stops attack  
Recon block = Nmap/IDS signatures  
C2 kill = network segmentation
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNjkzNTA5NzYsMTkyNzEyMTMxLC0xNT
k0MjAwOTI2LDQ0Mjg1MTUyMl19
-->