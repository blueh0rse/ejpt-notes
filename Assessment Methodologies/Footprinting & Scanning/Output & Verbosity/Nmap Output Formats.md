---
up: "[[Output & Verbosity]]"
---

# Nmap Output Formats

Always save all commands and output!

- Nmap formats:
	- `-oN`: normal
	- `-oX`: XML, importable into Metasploit
	- `-oS`: Script Kiddie
	- `-oG`: grepable
	- `-oA`: Output in normal, xml and grepable format

Normal format example:

```bash
nmap -oN normal_scan.txt <ip>
```

XML use case:

```bash
nmap -oX xml_scan.xml <ip>
```

Then import scan into Metasploit to save it:

```bash
$ msfconsole
# create workspace
msf6> workspace -a pentest_1
# import scan
msf6> db_import xml_scan.xml
# target is now added to hosts
msf6> hosts
...
msf6> services
...
# nmap scan from msf
msf6> db_nmap <ip>
```
