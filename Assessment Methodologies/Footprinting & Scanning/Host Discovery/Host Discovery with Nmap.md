---
up: "[[Host Discovery]]"
---

# Host Discovery with Nmap

Start [[nmap]] with `sudo` privileges.

```bash
man nmap

>/-sn
```

Scan a range:

```bash
nmap -sn 10.1.0.0/24
```

Target IPs list:

```txt
# targets.txt
10.10.10.1
10.10.10.2
10.10.10.3
...
```

Then:

```bash
nmap -sn -iL targets.txt
```

SYN scan is stealthier and faster:

```bash
nmap -sn -PS 10.10.10.10
```

Certain environment blocks ACK scan (`-PA`) so the best is still the SYN scan.

Good methodology:

```bash
nmap -sn -v -T4 <ip>
nmap -sn -PS -v -T4 <ip>
nmap -sn -PS -v -PU -T4 <ip>    # windows
```
