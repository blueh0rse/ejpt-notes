---
up: "[[4. ARCHIVES/eJPTv2/Assessment Methodologies/Enumeration/SSH/SSH|SSH]]"
---

# SSH - Introduction

Secure SHell. Interact with another machine using a secure connection.

```bash
nmap <ip>
```

Port 22 is open: default port for SSH.

```bash
nmap <ip> -sV -O
```

```bash
ssh root@<ip>
root@<ip>'s password: 
```

Banner grabbing:

```bash
nc <ip> 22
```

```bash
nmap <ip> -p 22 --script ssh2-enum-algos
nmap <ip> -p 22 --script ssh2-hostkey --script-args ssh_hostkey=full
```
