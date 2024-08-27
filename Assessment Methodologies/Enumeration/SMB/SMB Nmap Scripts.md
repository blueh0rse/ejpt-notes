---
up: "[[SMB]]"
---

# SMB Nmap Scripts

Start by a scan:

```bash
nmap <ip>
```

Port 445 is open (SMB). Let's enumerate a bit more:

- Protocol version used:

```bash
nmap -p 445 --script smb-protocols <ip>
```

- Security mode:

```bash
nmap -p 445 --script smb-security-mode <ip>
```

- enumerate sessions:

```bash
nmap -p 445 --script smb-enum-sessions <ip>
```

```bash
nmap -p 445 --script smb-enum-sessions --script-args ... <ip>
```

```bash
nmap -p 445 --script smb-enum-shares <ip>
```
