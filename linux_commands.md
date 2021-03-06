# Linux Commands
- Find files or directories \*\*[go-to](https://github.com/Snyd0g/Workflow_OSCP/blob/main/linux_commands.md#find-files-or-directories)
- Network Info \*\*[go-to](https://github.com/Snyd0g/Workflow_OSCP/blob/main/linux_commands.md#network-info)



## Find files or directories

*Basic search by case insensitive name using wildcards "\*" starting from root dir and redirecting errors, also runs an ls showing permissions*

`find / -iname '*name*' -ls 2>/dev/null`

*Find all nmap nse scripts related to http. Note I started the scan from /usr because I know my .nse scripts are located there. If you had no idea, you would use “/” as the 1st arg.*

`find /usr -iname '*.nse*' 2>/dev/null | grep http`

## Network Info

_Sockets and process ids (depending on user)_

`netstat -antup`

_lsof can accomplish a similar task using the following (in the strange event you don't have netstat)

`/usr/bin/lsof -ni :443`
