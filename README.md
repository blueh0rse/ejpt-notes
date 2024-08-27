# eJPT notes

This repository contains my raw notes compiled during the preparation for the eLearnSecurity Junior Penetration Tester (eJPT) certification. The notes encompass key concepts, commands, and methodologies relevant to the exam.

## Disclaimer

These notes are personal and informal. They are not a substitute for formal study materials and may contain inaccuracies. Users should cross-reference with official resources.

## Usage

These notes are structured by topic and are intended as a supplementary resource for eJPT exam preparation. Due to their raw nature, some sections may lack detailed explanations or contain incomplete information.

## Directory Structure

Below is the directory structure of the notes:

````text
.
├── Assessment Methodologies
│   ├── Assessment Methodologies.md
│   ├── Enumeration
│   │   ├── Enumeration.md
│   │   ├── FTP
│   │   │   ├── FTP - Anonymous Login.md
│   │   │   ├── FTP - Basics.md
│   │   │   └── FTP.md
│   │   ├── HTTP
│   │   │   ├── HTTP Apache.md
│   │   │   ├── HTTP IIS Nmap Scripts.md
│   │   │   ├── HTTP IIS.md
│   │   │   └── HTTP.md
│   │   ├── Introduction.md
│   │   ├── SMB
│   │   │   ├── SMB Dictionary Attack.md
│   │   │   ├── SMB Nmap Scripts.md
│   │   │   ├── SMB.md
│   │   │   ├── SMBMap.md
│   │   │   ├── Samba.md
│   │   │   └── Windows Discover & Mount.md
│   │   ├── SQL
│   │   │   ├── MSSQL Nmap Scripts.md
│   │   │   ├── MSSQL- Metasploit.md
│   │   │   ├── MySQL - Dictionary attack.md
│   │   │   ├── MySQL - Introduction.md
│   │   │   └── SQL.md
│   │   ├── SSH
│   │   │   ├── SSH - Dictionary Attack.md
│   │   │   ├── SSH - Introduction.md
│   │   │   └── SSH.md
│   │   └── Servers & Services.md
│   ├── Footprinting & Scanning
│   │   ├── Firewall Detection & IDS Evasion.md
│   │   ├── Footprinting & Scanning.md
│   │   ├── Host Discovery
│   │   │   ├── Host Discovery Techniques.md
│   │   │   ├── Host Discovery with Nmap.md
│   │   │   ├── Host Discovery.md
│   │   │   ├── Network Mapping.md
│   │   │   └── Ping Sweeps.md
│   │   ├── Introduction.md
│   │   ├── Networking Primer
│   │   │   ├── Network Layer.md
│   │   │   ├── Networking Fundamentals.md
│   │   │   ├── Networking Primer.md
│   │   │   └── Transport Layer.md
│   │   ├── Output & Verbosity
│   │   │   ├── Nmap Output Formats.md
│   │   │   ├── Output & Verbosity.md
│   │   │   └── 🧪 Windows Recon - SMB Nmap Scripts.md
│   │   ├── Port Scanning
│   │   │   ├── Nmap Scripting Engine.md
│   │   │   ├── Port Scanning.md
│   │   │   ├── Service Version & OS Detection.md
│   │   │   └── 🧪 Scan the Server.md
│   │   ├── Scan Timing and Performance.md
│   │   ├── Welcome.md
│   │   ├── 🧪 Scan the Server 2.md
│   │   └── 🧪 Windows Recon - Zenmap.md
│   ├── Information Gathering
│   │   ├── Active Information Gathering
│   │   │   ├── Active Information Gathering.md
│   │   │   ├── DNS Zone Transfers.md
│   │   │   ├── Host Discovery with Nmap.md
│   │   │   ├── Port Scanning With Nmap.md
│   │   │   └── 🧪 Windows Recon.md
│   │   ├── Information Gathering.md
│   │   ├── Introduction to Information Gathering.md
│   │   ├── Passive Information Gathering
│   │   │   ├── DNS Recon.md
│   │   │   ├── Email Harvesting With theHarvester.md
│   │   │   ├── Google Dorks.md
│   │   │   ├── Leaked Password Databases.md
│   │   │   ├── Passive Information Gathering.md
│   │   │   ├── Subdomain Enumeration with Sublist3r.md
│   │   │   ├── WAF with wafw00f.md
│   │   │   ├── Website Footprinting with Netcraft.md
│   │   │   ├── Website Recon & Footprinting.md
│   │   │   └── Whois Enumeration.md
│   │   └── Welcome.md
│   └── Vulnerability Assessment
│       ├── Case Studies.md
│       ├── Introduction.md
│       ├── Nessus introduction.md
│       ├── Vulnerability Assessment.md
│       ├── Vulnerability Overview.md
│       └── Vulnerability Research.md
├── Host & Network Penetration Testing
│   ├── Exploitation
│   │   ├── Exploitation Framework
│   │   │   ├── Exploitation Framework.md
│   │   │   ├── PowerShell Empire.md
│   │   │   └── The Metasploit Framework (MSF).md
│   │   ├── Exploitation.md
│   │   ├── Exploits
│   │   │   ├── Cross Compiling Exploits.md
│   │   │   ├── Exploits.md
│   │   │   ├── Fixing Exploits.md
│   │   │   ├── Searching for Exploits with Searchsploit.md
│   │   │   └── Searching for Publicly Available Exploits.md
│   │   ├── Introduction.md
│   │   ├── Linux Exploitation
│   │   │   ├── Linux Black Box Penetration Test.md
│   │   │   ├── Linux Exploitation.md
│   │   │   ├── Linux Port Scanning & Enumeration.md
│   │   │   ├── Targeting PHP.md
│   │   │   ├── Targeting SAMBA.md
│   │   │   └── Targeting vsFTPd.md
│   │   ├── Obfuscation
│   │   │   ├── AV Evasion with Shellter.md
│   │   │   ├── Obfuscating PowerShell Code.md
│   │   │   └── Obfuscation.md
│   │   ├── Shells
│   │   │   ├── Bind Shells.md
│   │   │   ├── Netcat Fundamentals.md
│   │   │   ├── Reverse Shell Cheatsheet.md
│   │   │   ├── Reverse Shell.md
│   │   │   └── Shells.md
│   │   ├── Vulnerability Scanning
│   │   │   ├── Banner Grabbing.md
│   │   │   ├── Vulnerability Scanning with Metasploit.md
│   │   │   ├── Vulnerability Scanning with Nmap Scripts.md
│   │   │   └── Vulnerability Scanning.md
│   │   └── Windows Exploitation
│   │       ├── Targeting Microsoft IIS FTP.md
│   │       ├── Targeting MySQL Database Server.md
│   │       ├── Targeting OpenSSH.md
│   │       ├── Targeting SMB.md
│   │       ├── Windows Black Box Penetration Test.md
│   │       ├── Windows Exploitation.md
│   │       └── Windows Port Scanning & Enumeration.md
│   ├── Host & Network Penetration Testing.md
│   ├── Network-Based Attacks
│   │   ├── ARP Poisoning.md
│   │   ├── Filtering Basics.md
│   │   ├── Filtering Wifi.md
│   │   ├── Introduction.md
│   │   ├── Network based attacks.md
│   │   ├── Network-Based Attacks.md
│   │   ├── Tshark.md
│   │   └── Wifi Traffic Analysis.md
│   ├── Post-Exploitation
│   │   ├── Clearing Tracks
│   │   │   ├── Clearing Tracks on Linux.md
│   │   │   ├── Clearing Tracks on Windows.md
│   │   │   └── Clearing Tracks.md
│   │   ├── Conclusion.md
│   │   ├── Dumping & Cracking Hashes
│   │   │   ├── Dumping & Cracking Hashes.md
│   │   │   ├── Linux Password Hashes.md
│   │   │   └── Windows NTLM Hashes.md
│   │   ├── Introduction.md
│   │   ├── Linux Local Enumeration
│   │   │   ├── Automating Linux Local Enumeration.md
│   │   │   ├── Enumerating Network Information.md
│   │   │   ├── Enumerating Processes & Cron Jobs.md
│   │   │   ├── Enumerating System Information.md
│   │   │   ├── Enumerating Users & Groups.md
│   │   │   └── Linux Local Enumeration.md
│   │   ├── Linux Persistence
│   │   │   ├── Linux Persistence.md
│   │   │   ├── Persistence via Cron Jobs.md
│   │   │   └── Persistence via SSH Keys.md
│   │   ├── Linux Privilege Escalation
│   │   │   ├── Linux Privilege Escalation.md
│   │   │   ├── SUDO Privileges.md
│   │   │   └── Weak Permissions.md
│   │   ├── Pivoting.md
│   │   ├── Post-Exploitation Introduction.md
│   │   ├── Post-Exploitation Methodology.md
│   │   ├── Post-Exploitation.md
│   │   ├── Transferring Files
│   │   │   ├── Setting up a Web Server with Python.md
│   │   │   ├── Transferring Files to Linux Targets.md
│   │   │   ├── Transferring Files to Windows Targets.md
│   │   │   └── Transferring Files.md
│   │   ├── Upgrading Non-Interactive Shells.md
│   │   ├── Windows Local Enumeration
│   │   │   ├── Automating Windows Local Enumeration.md
│   │   │   ├── Enumerating Network Information.md
│   │   │   ├── Enumerating Processes & Services.md
│   │   │   ├── Enumerating System Information.md
│   │   │   ├── Enumerating Users & Groups.md
│   │   │   └── Windows Local Enumeration.md
│   │   ├── Windows Persistence
│   │   │   ├── Persistence via RDP.md
│   │   │   ├── Persistence via Services.md
│   │   │   └── Windows Persistence.md
│   │   └── Windows Privilege Escalation
│   │       ├── Identifying Windows Privilege Escalation Vulnerabilities.md
│   │       ├── Windows PrivEsc.md
│   │       └── Windows Privilege Escalation.md
│   ├── Social Engineering
│   │   ├── Case Studies.md
│   │   ├── Let's goPhishing.md
│   │   ├── Penetration Testing and Social Engineering.md
│   │   ├── Social Engineering Fundamentals.md
│   │   └── Social Engineering.md
│   ├── System - Host Based Attacks
│   │   ├── Exploiting Linux Vulnerabilities
│   │   │   ├── Exploiting FTP.md
│   │   │   ├── Exploiting Linux Vulnerabilities.md
│   │   │   ├── Exploiting SAMBA.md
│   │   │   ├── Exploiting SSH.md
│   │   │   ├── Exploiting Shellshock Bash Vulnerability.md
│   │   │   └── Frequently Exploited Linux Services.md
│   │   ├── Exploiting Windows Vulnerabilities
│   │   │   ├── Exploiting Microsoft IIS & WebDAV.md
│   │   │   ├── Exploiting RDP.md
│   │   │   ├── Exploiting SMB with PsExec.md
│   │   │   ├── Exploiting WinRM.md
│   │   │   ├── Exploiting Windows BlueKeep RDP Vulnerability.md
│   │   │   ├── Exploiting Windows EternalBlue SMB Vulnerability.md
│   │   │   ├── Exploiting Windows Vulnerabilities.md
│   │   │   ├── 🧪 Windows ISS Server - DAVTest.md
│   │   │   ├── 🧪 Windows ISS Server - WebDAV Metasploit.md
│   │   │   ├── 🧪 Windows Insecure RDP Service.md
│   │   │   ├── 🧪 Windows SMB Server PSExec.md
│   │   │   └── 🧪 Windows WinRM Metasploit.md
│   │   ├── Host Based Attacks.md
│   │   ├── Introduction.md
│   │   ├── Linux Credential Dumping
│   │   │   ├── Dumping Linux Password Hashes.md
│   │   │   └── Linux Credential Dumping.md
│   │   ├── Linux Privilege Escalation
│   │   │   ├── Exploiting Misconfigured Con Jobs.md
│   │   │   ├── Exploiting SUID Binaries.md
│   │   │   ├── Linux Kernel Exploits.md
│   │   │   └── Linux Privilege Escalation.md
│   │   ├── System - Host Based Attacks.md
│   │   ├── Windows Credential Dumping
│   │   │   ├── Dumping Hashes with Mimikatz.md
│   │   │   ├── Pass-The-Hash Attacks.md
│   │   │   ├── Passwords in Windows Configuration File.md
│   │   │   ├── Windows Credential Dumping.md
│   │   │   ├── Windows Password Hashing.md
│   │   │   └── 🧪 Unattended Installation.md
│   │   ├── Windows File System Vulnerabilities
│   │   │   ├── Alternate Data Streams.md
│   │   │   └── Windows File System Vulnerabilities.md
│   │   ├── Windows Privilege Escalation
│   │   │   ├── Access Token Impersonation.md
│   │   │   ├── Bypassing UAC.md
│   │   │   ├── Windows Kernel Exploits.md
│   │   │   ├── Windows Privilege Escalation.md
│   │   │   ├── 🧪 Privilege Escalation Impersonate.md
│   │   │   └── 🧪 UAC Bypass UACMe.md
│   │   └── Windows Vulnerabilities.md
│   └── The Metasploit Framework
│       ├── Armitage
│       │   ├── Armitage.md
│       │   ├── Exploitation & Post Exploitation with Armitage.md
│       │   └── Port Scanning and Enumeration with Armitage.md
│       ├── Client-Side Attacks
│       │   ├── Automating Metasploit with Resources Scripts.md
│       │   ├── Client-Side Attacks.md
│       │   ├── Encoding Payloads with MSFvenom.md
│       │   ├── Generating Payloads with MSFvenom.md
│       │   └── Injecting Payloads into Windows Portables Executables.md
│       ├── Enumeration
│       │   ├── Enumeration.md
│       │   ├── FTP Enumeration.md
│       │   ├── MySQL Enumeration.md
│       │   ├── Port Scanning with Auxiliary Modules.md
│       │   ├── SMB Enumeration.md
│       │   ├── SMTP Enumeration.md
│       │   ├── SSH Enumeration.md
│       │   └── Web Server Enumeration.md
│       ├── Information Gathering
│       │   ├── Information Gathering.md
│       │   └── Nmap & MSF.md
│       ├── Introduction.md
│       ├── Linux Exploitation
│       │   ├── Exploiting SSH.md
│       │   ├── Exploiting Samba.md
│       │   ├── Exploiting a Vulnerable FTP Server.md
│       │   ├── Exploiting a Vulnerable SMTP Server.md
│       │   └── Linux Exploitation.md
│       ├── Linux Post Exploitation
│       │   ├── Dumping Hashes with Hashdump.md
│       │   ├── Establishing Persistence on Linux.md
│       │   ├── Exploiting a Vulnerable Program.md
│       │   ├── Linux Post Exploitation Modules.md
│       │   └── Linux Post Exploitation.md
│       ├── Metasploit Fundamentals.md
│       ├── Metasploit Overview.md
│       ├── Post Exploitation Fundamentals
│       │   ├── Meterpreter Fundamentals.md
│       │   ├── Post Exploitation Fundamentals.md
│       │   └── Upgrading Command Shells to Meterpreter Shells.md
│       ├── The Metasploit Framework.md
│       ├── Vulnerability Scanning
│       │   ├── Vulnerability Scanning with MSF.md
│       │   ├── Vulnerability Scanning with Nessus.md
│       │   ├── Vulnerability Scanning.md
│       │   └── Web App Vulnerability Scanning with WMAP.md
│       ├── Windows Exploitation
│       │   ├── Exploiting Apache Tomcat Server.md
│       │   ├── Exploiting WinRM.md
│       │   ├── Exploiting Windows MS17-010 SMB Vulnerability.md
│       │   ├── Exploiting a Vulnerable HTTP File Server.md
│       │   └── Windows Exploitation.md
│       └── Windows Post Exploitation
│           ├── Bypassing UAC.md
│           ├── Clearing Windows Event Logs.md
│           ├── Dumping Hashes with Mimikatz.md
│           ├── Enabling RDP.md
│           ├── Establishing Persistence on Windows.md
│           ├── Pass-the-hash with PSExec.md
│           ├── Pivoting.md
│           ├── Token Impersonation with Incognito.md
│           ├── Windows Keylogging.md
│           ├── Windows Post Exploitation Modules.md
│           ├── Windows Post Exploitation.md
│           └── 🧪 Pivoting.md
├── Host & Networking Auditing
│   ├── Auditing Fundamentals
│   │   ├── Auditing
│   │   │   └── Auditing.md
│   │   ├── Auditing Fundamentals.md
│   │   ├── Introduction.md
│   │   └── Practice
│   │       └── Practice.md
│   └── Host & Networking Auditing.md
├── Web Application Penetration Testing
│   ├── Conclusion.md
│   ├── Introduction to Web and HTTP Protocol
│   │   ├── Attacking Basic Auth with Burp Suite.md
│   │   ├── Attacking HTTP Login Form with Hydra.md
│   │   ├── Attacking HTTP Login Form with ZAP.md
│   │   ├── Authenticated XSS Attack with XSSer.md
│   │   ├── Directory Enumeration with Burp Suite.md
│   │   ├── Directory Enumeration with Gobuster.md
│   │   ├── Introduction to Web and HTTP Protocol.md
│   │   ├── Introduction to Web.md
│   │   ├── Introduction.md
│   │   ├── Passive Crawling with Burp Suite.md
│   │   ├── SQL Injection with SQLMap.md
│   │   ├── Scanning Web Application with Nikto.md
│   │   ├── Scanning Web Application with ZAP.md
│   │   ├── Web and HTTP Protocol.md
│   │   └── XSS Attack with XSSer.md
│   └── Web Application Penetration Testing.md
└── eJPTv2.md

62 directories, 283 files
````
