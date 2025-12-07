## Basics

- System information 
	- systeminfo
	- pipe it with more to view in page by page mode with a space
- Network 
	- ipconfig
		- add help for help, and /all for more info
	- tracert
		- trace route- traces the path traversed to reach the destination
	- nslookup 
		- looks up host or domain and returns its ip 
		- The syntax `nslookup example.com` will look up `example.com` using the default name server; however, `nslookup example.com 1.1.1.1` will use the name server `one.one.one.one`
	- netstat
		- displays current network connections and listening ports
		- -h for help, look out for a (all), b (program associated), o (PID), n (numerical form), netstat -abon for short
- Linux equivalent
	- pwd - cd
	- ls 
		- dir for directories
			- /a for hidden and system files
			- /s for files in current dir and all subdir
		- tree for visual representation
	- cat - type for short, pipe to more for long
	- touch
		- echo text > text.txt 
		- echo: > text.txt for empty file
		- yeah it sucks, didn't find a direct touch command 
	- mv - move
	- rm - del or e
	- 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkyNDg3MTA2NywtMzQ4MzkwNzI2XX0=
-->