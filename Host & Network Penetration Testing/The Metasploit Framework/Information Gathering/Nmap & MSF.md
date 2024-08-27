---
up: "[[4. ARCHIVES/eJPTv2/Host & Network Penetration Testing/The Metasploit Framework/Information Gathering/Information Gathering|Information Gathering]]"
---

# Nmap & MSF

## Port Scanning

- We can output the results of our nmap scan into a format that can be imported into MSF for vulnerability detection and exploitation

```bash
nmap <ip> -oX scan.xml
```

## Importing Nmap scan into MSF

```bash
# import nmap scan
> db_import ~/scan.xml
# show host(s)
> hosts
# show services
> services
# show vulnerabilities
> vulns
```

Directly perform an nmap scan in MSF:

```bash
> db_nmap -sV -O <ip>
```
