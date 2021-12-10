# Linux Commands
- Find files or directories \*\*[go-to](https://github.com/Snyd0g/Workflow_OSCP/blob/main/linux_commands.md#find-files-or-directories)
- Network Info \*\*[go-to](https://github.com/Snyd0g/Workflow_OSCP/blob/main/linux_commands.md#network-info)

- Services \*\*[go-to](https://github.com/Snyd0g/Workflow_OSCP/blob/main/linux_commands.md#services)

- Users, Groups, Policies \*\*[go-to](https://github.com/Snyd0g/Workflow_OSCP/blob/main/linux_commands.md#users-groups-policies)

## Find files or directories

*Basic search by case insensitive name using wildcards "\*" starting from root dir and redirecting errors, also runs an ls showing permissions*

`find / -iname '*name*' -ls 2>/dev/null`

*Find all nmap nse scripts related to http. Note I started the scan from /usr because I know my .nse scripts are located there. If you had no idea, you would use “/” as the 1st argument.*

`find /usr -iname '*.nse*' 2>/dev/null | grep http`

*Find all .txt files excluding /sys /run /proc directories from the search*

`sudo find / -type d \( -path /sys -o -path /run -o -path /proc \) -prune -o -name "*.txt"`

## Network Info

_Sockets and process IDs_

`sudo netstat -antup`

_- or if netstat is not there_

`sudo ss -antup`

_lsof can accomplish a similar task using the following (in the strange event you don't have netstat or ss)_

`/usr/bin/lsof -ni :443`

## Process info

`ps -elf`

_Find a specific process by it's process ID (example with a process id of 1337)_

`ps -elf | grep 1337`

## Services

_The following will list all of the loaded services and display their state i.e. (active, running, listening, waiting)_

`sudo systemctl list-units`

## Users, Groups, Policies

_To view the current password policies you can use the command less to open the /etc/login.defs file. Searching the output is possible by pressing the "/" key and then typing the text you wish to search for. For instance, if I was looking for the max password age I would type "/MAX" and press enter. Then you can simply hit the up and down arrow keys to move around the file._ 

`less /etc/login.defs`

_If you need to make changes to the system policies you would need to edit the /etc/login.defs file by using vim or nano_

`sudo nano /etc/login.defs` 

_Modifying one user can be accomplished by using the usermod command. The following example would lock the user account morty._

`sudo usermod -L morty`

