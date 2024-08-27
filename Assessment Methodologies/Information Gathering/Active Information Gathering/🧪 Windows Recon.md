---
up: "[[Active Information Gathering]]"
---

# 🧪 Windows Recon: Nmap Host Discovery

## Overview

A Kali GUI machine and a target machine are provided to you. The target machine is running a Windows Firewall. 

Your task is to discover available live hosts and their open ports using Nmap and identify the running services and applications.

## Tasks

- [-] Your Kali machine has an interface with IP address 10.10.X.Y. Run `ip addr` to know the values of X and Y.
- [-] The IP address of the target machine is mentioned in the file `/root/Desktop/target`
- [-] Do not attack the gateway located at IP address 192.V.W.1 and 10.10.X.1

## Solution

```bash
$ ip addr
269313: eth0@if269314: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:0a:01:00:04 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 10.1.0.4/16 brd 10.1.255.255 scope global eth0
       valid_lft forever preferred_lft forever
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: ip_vti0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN group default qlen 1000
    link/ipip 0.0.0.0 brd 0.0.0.0
269315: eth1@if269316: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:0a:0a:18:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 10.10.24.2/24 brd 10.10.24.255 scope global eth1
       valid_lft forever preferred_lft forever
```

> [!success] Task 1
> My IP address is ``10.10.24.2``

```bash
$ cat /root/Desktop/target 
Target IP Address : 10.2.19.221
```

> [!success] Task 2
> Target IP Address is `10.2.19.221`

```bash
$ nmap 10.2.19.221
Starting Nmap 7.70 ( https://nmap.org ) at 2024-01-15 03:33 IST
Note: Host seems down. If it is really up, but blocking our ping probes, try -Pn
Nmap done: 1 IP address (0 hosts up) scanned in 3.12 seconds

$ nmap -Pn 10.2.19.221
Starting Nmap 7.70 ( https://nmap.org ) at 2024-01-15 03:33 IST
Nmap scan report for 10.2.19.221
Host is up (0.0028s latency).
Not shown: 993 filtered ports
PORT      STATE SERVICE
80/tcp    open  http
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
3389/tcp  open  ms-wbt-server
49154/tcp open  unknown
49155/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 4.87 seconds

$ nmap -Pn -sV 10.2.19.221
Starting Nmap 7.70 ( https://nmap.org ) at 2024-01-15 03:34 IST
Nmap scan report for 10.2.19.221
Host is up (0.0023s latency).
Not shown: 993 filtered ports
PORT      STATE SERVICE            VERSION
80/tcp    open  http               HttpFileServer httpd 2.3
135/tcp   open  msrpc              Microsoft Windows RPC
139/tcp   open  netbios-ssn        Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds       Microsoft Windows Server 2008 R2 - 2012 microsoft-ds
3389/tcp  open  ssl/ms-wbt-server?
49154/tcp open  msrpc              Microsoft Windows RPC
49155/tcp open  msrpc              Microsoft Windows RPC
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 79.97 seconds
```

> [!success] Task 3
> Open ports are `80, 135, 139, 445, 3389, 49154, 49155`
