---
up: "[[Port Scanning]]"
---

# Nmap Scripting Engine

1. Scan the whole network
2. Scan more precisely the target
	- `-sS`
	- `-sV`
	- `-O`
	- `-p-`
	- `-T4`

What is NSE?

- Write and share automated tasks:
	- port scanning
	- vuln scanning
	- brute-forcing...
- Huge library of scripts
	- Located in `/usr/share/nmap/scripts`
- Written in LUA programming languages
- Search for specific scripts:

```bash
ls -al /usr/share/nmap/scripts | grep -e "http"
```

- Organized in categories:
	- `auth`: 
	- `cast`:
	- `brute`:
	- `default`: default scripts used with `-sC`. Safe to run.

In Information Gathering phase we don't want to run any script exploiting a vulnerability.

A lot of information can be revealed from services.

Get information about a specific script:

```bash
nmap --script-help=mongodb-databases
```

Run a specific script:

```bash
nmap --script=<script1>[,<script2>,<script3>] <ip>
```

Run a category of scripts:

```bash
nmap --script=ftp-* <ip>
```
