---
up: "[[Footprinting & Scanning]]"
---

# 🧪 Scan the Server 2

This lab covers the process of performing port scanning and service detection with Nmap.

The objectives of this lab are to:

1. Identify the port running a Bind DNS server.
2. Identify the port running a TFTP server.
3. Identify the port running the SNMP server.

```bash
# nmap -sS -p- $TRG
Starting Nmap 7.92 ( https://nmap.org ) at 2024-01-27 04:46 IST
Nmap scan report for 7q14ke61j8lh9tg8eb6gouq8g.temp-network_a-247-75 (192.247.75.3)
Host is up (0.0000090s latency).
Not shown: 65534 closed tcp ports (reset)
PORT    STATE SERVICE
177/tcp open  xdmcp
MAC Address: 02:42:C0:F7:4B:03 (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 1.30 seconds
```

```bash
# nmap -sC -sV -p- $TRG
Starting Nmap 7.92 ( https://nmap.org ) at 2024-01-27 04:49 IST
Nmap scan report for 7q14ke61j8lh9tg8eb6gouq8g.temp-network_a-247-75 (192.247.75.3)
Host is up (0.000010s latency).
Not shown: 65534 closed tcp ports (reset)
PORT    STATE SERVICE VERSION
177/tcp open  domain  ISC BIND 9.10.3-P4 (Ubuntu Linux)
| dns-nsid: 
|_  bind.version: 9.10.3-P4-Ubuntu
MAC Address: 02:42:C0:F7:4B:03 (Unknown)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 40.87 seconds
```
