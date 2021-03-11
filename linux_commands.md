# Linux Commands
- Find files or directories



## Find files or directories

*Basic search by case insensitive name using wildcards "\*" starting from root dir and redirecting errors, also runs an ls showing permissions*

`find / -iname '*name*' -ls 2>/dev/null`

*Find all nmap nse scripts related to http. Note I started the scan from /usr because I know my .nse scripts are located there. If you had no idea, you would use “/” as the 1st arg.*

`find /usr -iname '*.nse*' 2>/dev/null | grep http`
