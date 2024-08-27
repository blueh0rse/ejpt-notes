---
up: "[[Output & Verbosity]]"
---

# 🧪 Windows Recon - SMB Nmap Scripts

Your task is to fingerprint the service using the tools available on the Kali machine and run Nmap scripts to enumerate the Windows target machine SMB service.

**Objective:**

1. Identify SMB Protocol Dialects
2. Find SMB security level information
3. Enumerate active sessions, shares, Windows users, domains, services, etc.

Solution:

Target IP is 10.4.26.81.

Basic scan:

```bash
# nmap 10.4.26.81
Starting Nmap 7.91 ( https://nmap.org ) at 2024-01-27 03:09 IST
Nmap scan report for 10.4.26.81
Host is up (0.0085s latency).
Not shown: 992 closed ports
PORT      STATE SERVICE
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
3389/tcp  open  ms-wbt-server
49152/tcp open  unknown
49153/tcp open  unknown
49154/tcp open  unknown
49155/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 1.55 seconds
```

All ports scan:

```bash
# nmap -p- 10.4.26.81
Starting Nmap 7.91 ( https://nmap.org ) at 2024-01-27 03:10 IST
Nmap scan report for 10.4.26.81
Host is up (0.0089s latency).
Not shown: 65523 closed ports
PORT      STATE SERVICE
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
3389/tcp  open  ms-wbt-server
5985/tcp  open  wsman
47001/tcp open  winrm
49152/tcp open  unknown
49153/tcp open  unknown
49154/tcp open  unknown
49155/tcp open  unknown
49164/tcp open  unknown
49180/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 20.91 seconds
```

Service Version scan:

```bash
# nmap -sV -p- -oN scan2.txt 10.4.26.81
Starting Nmap 7.91 ( https://nmap.org ) at 2024-01-27 03:15 IST
Nmap scan report for 10.4.26.81
Host is up (0.0090s latency).
Not shown: 65523 closed ports
PORT      STATE SERVICE            VERSION
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
49164/tcp open  msrpc              Microsoft Windows RPC
49180/tcp open  msrpc              Microsoft Windows RPC
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 86.87 seconds
```

Aggressive scan:

```bash
# nmap -A -p- -oN scan.txt 10.4.26.81
Starting Nmap 7.91 ( https://nmap.org ) at 2024-01-27 03:11 IST
Stats: 0:00:55 elapsed; 0 hosts completed (1 up), 1 undergoing Service Scan
Service scan Timing: About 41.67% done; ETC: 03:12 (0:00:49 remaining)
Nmap scan report for 10.4.26.81
Host is up (0.0085s latency).
Not shown: 65523 closed ports
PORT      STATE SERVICE            VERSION
135/tcp   open  msrpc              Microsoft Windows RPC
139/tcp   open  netbios-ssn        Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds       Windows Server 2012 R2 Standard 9600 microsoft-ds
3389/tcp  open  ssl/ms-wbt-server?
| rdp-ntlm-info: 
|   Target_Name: WIN-OMCNBKR66MN
|   NetBIOS_Domain_Name: WIN-OMCNBKR66MN
|   NetBIOS_Computer_Name: WIN-OMCNBKR66MN
|   DNS_Domain_Name: WIN-OMCNBKR66MN
|   DNS_Computer_Name: WIN-OMCNBKR66MN
|   Product_Version: 6.3.9600
|_  System_Time: 2024-01-26T21:42:40+00:00
| ssl-cert: Subject: commonName=WIN-OMCNBKR66MN
| Not valid before: 2024-01-25T21:38:04
|_Not valid after:  2024-07-26T21:38:04
5985/tcp  open  http               Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
47001/tcp open  http               Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
49152/tcp open  msrpc              Microsoft Windows RPC
49153/tcp open  msrpc              Microsoft Windows RPC
49154/tcp open  msrpc              Microsoft Windows RPC
49155/tcp open  msrpc              Microsoft Windows RPC
49164/tcp open  msrpc              Microsoft Windows RPC
49180/tcp open  msrpc              Microsoft Windows RPC
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.91%E=4%D=1/27%OT=135%CT=1%CU=40881%PV=Y%DS=3%DC=T%G=Y%TM=65B427
OS:59%P=x86_64-pc-linux-gnu)SEQ(SP=101%GCD=1%ISR=109%TI=I%CI=I%II=I%SS=S%TS
OS:=7)OPS(O1=M546NW8ST11%O2=M546NW8ST11%O3=M546NW8NNT11%O4=M546NW8ST11%O5=M
OS:546NW8ST11%O6=M546ST11)WIN(W1=2000%W2=2000%W3=2000%W4=2000%W5=2000%W6=20
OS:00)ECN(R=Y%DF=Y%T=7F%W=2000%O=M546NW8NNS%CC=Y%Q=)T1(R=Y%DF=Y%T=7F%S=O%A=
OS:S+%F=AS%RD=0%Q=)T2(R=Y%DF=Y%T=7F%W=0%S=Z%A=S%F=AR%O=%RD=0%Q=)T3(R=Y%DF=Y
OS:%T=7F%W=0%S=Z%A=O%F=AR%O=%RD=0%Q=)T4(R=Y%DF=Y%T=7F%W=0%S=A%A=O%F=R%O=%RD
OS:=0%Q=)T5(R=Y%DF=Y%T=7F%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=7F%W=0
OS:%S=A%A=O%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=7F%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1
OS:(R=Y%DF=N%T=7F%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI
OS:=N%T=7F%CD=Z)

Network Distance: 3 hops
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: 0s, deviation: 3s, median: -1s
| smb-os-discovery: 
|   OS: Windows Server 2012 R2 Standard 9600 (Windows Server 2012 R2 Standard 6.3)
|   OS CPE: cpe:/o:microsoft:windows_server_2012::-
|   Computer name: WIN-OMCNBKR66MN
|   NetBIOS computer name: WIN-OMCNBKR66MN\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2024-01-26T21:42:45+00:00
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2024-01-26T21:42:41
|_  start_date: 2024-01-26T21:36:41

TRACEROUTE (using port 256/tcp)
HOP RTT     ADDRESS
1   0.02 ms us-east-7 (10.10.22.1)
2   ...
3   8.72 ms 10.4.26.81

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 108.18 seconds
```

Let's use some nmap smb scripts:

```bash
# ll /usr/share/nmap/scripts | grep smb-enum
-rw-r--r-- 1 root root  4840 Oct 12  2020 smb-enum-domains.nse
-rw-r--r-- 1 root root  5971 Oct 12  2020 smb-enum-groups.nse
-rw-r--r-- 1 root root  8043 Oct 12  2020 smb-enum-processes.nse
-rw-r--r-- 1 root root 27274 Oct 12  2020 smb-enum-services.nse
-rw-r--r-- 1 root root 12097 Oct 12  2020 smb-enum-sessions.nse
-rw-r--r-- 1 root root  6923 Oct 12  2020 smb-enum-shares.nse
-rw-r--r-- 1 root root 12527 Oct 12  2020 smb-enum-users.nse
```

```bash
# nmap -p 445 --script=smb-enum-* --script-args smbusername=administrator,smbpassword=smbserver_771 10.4.26.81
Starting Nmap 7.91 ( https://nmap.org ) at 2024-01-27 03:37 IST
Nmap scan report for 10.4.26.81
Host is up (0.0076s latency).

PORT    STATE SERVICE
445/tcp open  microsoft-ds
| smb-enum-services: 
|   AmazonSSMAgent: 
|     display_name: Amazon SSM Agent
|     state: 
|       SERVICE_PAUSED
|       SERVICE_RUNNING
|       SERVICE_PAUSE_PENDING
|       SERVICE_CONTINUE_PENDING
|     type: 
|       SERVICE_TYPE_WIN32
|       SERVICE_TYPE_WIN32_OWN_PROCESS
|     controls_accepted: 
|       SERVICE_CONTROL_PARAMCHANGE
|       SERVICE_CONTROL_NETBINDENABLE
|       SERVICE_CONTROL_NETBINDADD
|       SERVICE_CONTROL_CONTINUE
|       SERVICE_CONTROL_INTERROGATE
|       SERVICE_CONTROL_STOP
|   DiagTrack: 
|     display_name: Diagnostics Tracking Service
|     state: 
|       SERVICE_PAUSED
|       SERVICE_RUNNING
|       SERVICE_PAUSE_PENDING
|       SERVICE_CONTINUE_PENDING
|     type: 
|       SERVICE_TYPE_WIN32
|       SERVICE_TYPE_WIN32_OWN_PROCESS
|     controls_accepted: 
|       SERVICE_CONTROL_PARAMCHANGE
|       SERVICE_CONTROL_NETBINDENABLE
|       SERVICE_CONTROL_NETBINDADD
|       SERVICE_CONTROL_CONTINUE
|       SERVICE_CONTROL_INTERROGATE
|       SERVICE_CONTROL_STOP
|   Ec2Config: 
|     display_name: Ec2Config
|     state: 
|       SERVICE_PAUSED
|       SERVICE_RUNNING
|       SERVICE_PAUSE_PENDING
|       SERVICE_CONTINUE_PENDING
|     type: 
|       SERVICE_TYPE_WIN32
|       SERVICE_TYPE_WIN32_OWN_PROCESS
|     controls_accepted: 
|       SERVICE_CONTROL_PARAMCHANGE
|       SERVICE_CONTROL_NETBINDENABLE
|       SERVICE_CONTROL_NETBINDADD
|       SERVICE_CONTROL_CONTINUE
|       SERVICE_CONTROL_INTERROGATE
|       SERVICE_CONTROL_STOP
|   MSDTC: 
|     display_name: Distributed Transaction Coordinator
|     state: 
|       SERVICE_PAUSED
|       SERVICE_RUNNING
|       SERVICE_PAUSE_PENDING
|       SERVICE_CONTINUE_PENDING
|     type: 
|       SERVICE_TYPE_WIN32
|       SERVICE_TYPE_WIN32_OWN_PROCESS
|     controls_accepted: 
|       SERVICE_CONTROL_PARAMCHANGE
|       SERVICE_CONTROL_NETBINDENABLE
|       SERVICE_CONTROL_NETBINDADD
|       SERVICE_CONTROL_CONTINUE
|       SERVICE_CONTROL_INTERROGATE
|       SERVICE_CONTROL_STOP
|   Spooler: 
|     display_name: Print Spooler
|     state: 
|       SERVICE_PAUSED
|       SERVICE_RUNNING
|       SERVICE_PAUSE_PENDING
|       SERVICE_CONTINUE_PENDING
|     type: 
|       SERVICE_TYPE_WIN32
|       SERVICE_TYPE_WIN32_OWN_PROCESS
|     controls_accepted: 
|       SERVICE_CONTROL_NETBINDENABLE
|       SERVICE_CONTROL_NETBINDADD
|       SERVICE_CONTROL_CONTINUE
|_      SERVICE_CONTROL_STOP

Host script results:
| smb-enum-domains: 
|   WIN-OMCNBKR66MN
|     Groups: WinRMRemoteWMIUsers__
|     Users: Administrator, bob, Guest
|     Creation time: 2013-08-22T14:47:57
|     Passwords: min length: n/a; min age: n/a days; max age: 42 days; history: n/a passwords
|     Properties: Complexity requirements exist
|     Account lockout disabled
|   Builtin
|     Groups: Access Control Assistance Operators, Administrators, Backup Operators, Certificate Service DCOM Access, Cryptographic Operators, Distributed COM Users, Event Log Readers, Guests, Hyper-V Administrators, IIS_IUSRS, Network Configuration Operators, Performance Log Users, Performance Monitor Users, Power Users, Print Operators, RDS Endpoint Servers, RDS Management Servers, RDS Remote Access Servers, Remote Desktop Users, Remote Management Users, Replicator, Users
|     Users: n/a
|     Creation time: 2013-08-22T14:47:57
|     Passwords: min length: n/a; min age: n/a days; max age: 42 days; history: n/a passwords
|_    Account lockout disabled
| smb-enum-groups: 
|   Builtin\Administrators (RID: 544): Administrator, bob
|   Builtin\Users (RID: 545): bob
|   Builtin\Guests (RID: 546): Guest
|   Builtin\Power Users (RID: 547): <empty>
|   Builtin\Print Operators (RID: 550): <empty>
|   Builtin\Backup Operators (RID: 551): <empty>
|   Builtin\Replicator (RID: 552): <empty>
|   Builtin\Remote Desktop Users (RID: 555): bob
|   Builtin\Network Configuration Operators (RID: 556): <empty>
|   Builtin\Performance Monitor Users (RID: 558): <empty>
|   Builtin\Performance Log Users (RID: 559): <empty>
|   Builtin\Distributed COM Users (RID: 562): <empty>
|   Builtin\IIS_IUSRS (RID: 568): <empty>
|   Builtin\Cryptographic Operators (RID: 569): <empty>
|   Builtin\Event Log Readers (RID: 573): <empty>
|   Builtin\Certificate Service DCOM Access (RID: 574): <empty>
|   Builtin\RDS Remote Access Servers (RID: 575): <empty>
|   Builtin\RDS Endpoint Servers (RID: 576): <empty>
|   Builtin\RDS Management Servers (RID: 577): <empty>
|   Builtin\Hyper-V Administrators (RID: 578): <empty>
|   Builtin\Access Control Assistance Operators (RID: 579): <empty>
|   Builtin\Remote Management Users (RID: 580): <empty>
|_  WIN-OMCNBKR66MN\WinRMRemoteWMIUsers__ (RID: 1000): <empty>
| smb-enum-sessions: 
|   Users logged in
|     WIN-OMCNBKR66MN\bob since 2024-01-26T21:38:05
|   Active SMB sessions
|     ADMINISTRATOR is connected from \\10.10.22.13 for 10s, idle for 10s
|     ADMINISTRATOR is connected from \\10.10.22.13 for 3s, idle for 3s
|_    ADMINISTRATOR is connected from \\10.10.22.13 for [just logged in, its probably you], idle for [not idle]
| smb-enum-shares: 
|   account_used: administrator
|   \\10.4.26.81\ADMIN$: 
|     Type: STYPE_DISKTREE_HIDDEN
|     Comment: Remote Admin
|     Users: 0
|     Max Users: <unlimited>
|     Path: C:\Windows
|     Anonymous access: <none>
|     Current user access: READ/WRITE
|   \\10.4.26.81\C: 
|     Type: STYPE_DISKTREE
|     Comment: 
|     Users: 0
|     Max Users: <unlimited>
|     Path: C:\
|     Anonymous access: <none>
|     Current user access: READ
|   \\10.4.26.81\C$: 
|     Type: STYPE_DISKTREE_HIDDEN
|     Comment: Default share
|     Users: 0
|     Max Users: <unlimited>
|     Path: C:\
|     Anonymous access: <none>
|     Current user access: READ/WRITE
|   \\10.4.26.81\D$: 
|     Type: STYPE_DISKTREE_HIDDEN
|     Comment: Default share
|     Users: 0
|     Max Users: <unlimited>
|     Path: D:\
|     Anonymous access: <none>
|     Current user access: READ/WRITE
|   \\10.4.26.81\Documents: 
|     Type: STYPE_DISKTREE
|     Comment: 
|     Users: 0
|     Max Users: <unlimited>
|     Path: C:\Users\Administrator\Documents
|     Anonymous access: <none>
|     Current user access: READ
|   \\10.4.26.81\Downloads: 
|     Type: STYPE_DISKTREE
|     Comment: 
|     Users: 0
|     Max Users: <unlimited>
|     Path: C:\Users\Administrator\Downloads
|     Anonymous access: <none>
|     Current user access: READ
|   \\10.4.26.81\IPC$: 
|     Type: STYPE_IPC_HIDDEN
|     Comment: Remote IPC
|     Users: 1
|     Max Users: <unlimited>
|     Path: 
|     Anonymous access: <none>
|     Current user access: READ/WRITE
|   \\10.4.26.81\print$: 
|     Type: STYPE_DISKTREE
|     Comment: Printer Drivers
|     Users: 0
|     Max Users: <unlimited>
|     Path: C:\Windows\system32\spool\drivers
|     Anonymous access: <none>
|_    Current user access: READ/WRITE
| smb-enum-users: 
|   WIN-OMCNBKR66MN\Administrator (RID: 500)
|     Description: Built-in account for administering the computer/domain
|     Flags:       Normal user account, Password does not expire
|   WIN-OMCNBKR66MN\bob (RID: 1010)
|     Flags:       Normal user account, Password does not expire
|   WIN-OMCNBKR66MN\Guest (RID: 501)
|     Description: Built-in account for guest access to the computer/domain
|_    Flags:       Normal user account, Password not required, Password does not expire

Nmap done: 1 IP address (1 host up) scanned in 62.65 seconds
```
