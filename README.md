# Workflow_OSCP
**Ways to keep on track in PWK**  _The purpose of this is to better our process, and enable us to work together contributing to one another's success. Please remember, this doc will not be all-inclusive or cover every aspect you may encounter. It is mearly there to remind you of the process and help when your nerves make your brain forget a useful command._ **This is a work in progress and I'm sharing now to encorage collaboration.**

## Initial Enumeration

### Scans 
*First thing I do on target is scan all tcp ports to see what's open. Flags: -n (no DNS) -p- (all 65535 TCP) -Pn (no ping) -sS (syn stealth/default for root/see man page for more) -oN (output to file and avoid repeating the same scan)*
    
`sudo nmap -n -p- -Pn -sS -oN out.file <ip>`
       
*Odds are you'll have something to go after with that info. Otherwise one could do a UDP scan to be thorough.*
    
`sudo nmap -n -sU -Pn -oN out.UDP <ip>`
    
*Take your output file and pull all the ports out in a nice little comma separated line. Not nessasary but saves a little time typing since you can just cp/paste the output of this bad boy. Works on -oN output files.*
    
`cat <out.file> | egrep '^[1-9]' | cut -d '/' -f 1 | tr '\n' ','| awk '{print substr($0, 1, length($0)-1)}'`
    
*If you have a list of ports to go deeper on now's the time to enumerate services if possible*
    
`sudo nmap -n -Pn -p <pasted output from command above> -sV --version-all -sC -oN <service.ScanName> <ip>`
