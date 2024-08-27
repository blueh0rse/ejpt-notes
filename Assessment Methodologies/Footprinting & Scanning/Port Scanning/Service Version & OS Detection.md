---
up: "[[Port Scanning]]"
---

# Service Version & OS Detection

```bash
nmap -sn 10.10.10.0/24
```

```bash
nmap -sS 10.10.10.10
```

Recommended to scan all ports:

```bash
nmap -sS -p- -T4 10.10.10.10
```

Service Version Detection:

```bash
nmap -sS -sV -p- -T4 10.10.10.10
```

```bash
nmap -sV --version-intensity 9    # from 1 to 9
```

Operating System Detection:

```bash
nmap -sV -O 10.10.10.10
```

Aggressive detection:

```bash
nmap -O --osscan-guess <ip>
```
