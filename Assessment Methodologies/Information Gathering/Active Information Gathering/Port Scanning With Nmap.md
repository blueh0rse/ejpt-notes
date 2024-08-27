---
up: "[[Active Information Gathering]]"
---

# Port Scanning With Nmap

Objective: obtain as much information as possible using `nmap` port scanning.

Default nmap scan:

```bash
nmap <ip>
```

is a SYN scan on the most common 1000 ports.

If host looks down use option `-Pn` to disable isAlive check, usually happen with Windows machines.

- Scan all ports with `-p-` option.
- Scan specific ports with `-p 80,443` for example

- To do a UDP scan use `-sU` option

Always useful to do a UDP port scan as some specific services use it.

- `-sV` to perform service version scan
- `-O` to try to identify running Operating System
- `-sC` default nmap scripts to get more information from open ports

- `-A` aggressive scan combining `-sV -sC -O`
- `-T0` to scan very sneakily
- `-T5` to scan very aggressively

- `-oN file.txt` to save output in text format
- `-oX file.xml` to save output in xml format
	- Can be imported in Metasploit
