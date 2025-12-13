## Powershell

- Basic commands
	- It's all case insensitive
	- Get-Help is like man
		- look at the bottom, you'll see useful stuff like -examples
	- Get-Alias to list all alias
		- then you can use stuff  like ls, cd and man
	- Get-Command to list all commands
	- Set-PSReadLineOption -EditMode Emacs to use keybindings like ctrl b,p,a,k,f
	- NewItem to create an item (or just ni)
		- New-Item -Path ".\captain-cabin\captain-wardrobe" -ItemType "Directory"
	- Select-Object (or select) to select specific stuff
		- ls | select name, length
	- Select-String (or sls) - like grep 
		- `alias | sls sls` - why this shows only "sls" and not the full row like grep :
		- The `alias` cmdlet outputs objects with properties like Name, CommandType, and Definition, not plain text lines. When piped to `sls`, it matches on the string "sls" (typically in the Name property) but displays a formatted summary rather than the full object details, unlike `grep`'s line-based output on text streams.
	- Where-Object to filter stuff out
		- ls | where-object -property "length" -gt 100
		- or just ls | ? length -gt 100
- System Information 
	- Get-ComputerInfo
	- like systeminfo in cmd, but more detailed
- 


<!--stackedit_data:
eyJoaXN0b3J5IjpbODk1ODUwNDE5LDIxMjY2OTEwODIsMTg3OD
IzODg2M119
-->