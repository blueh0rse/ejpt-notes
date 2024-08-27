---
up: "[[Active Information Gathering]]"
---

# Host Discovery with Nmap

Identify my IP address:

```bash
ip ad
```

[[nmap]] is an open source tool for network exploration.

```bash
sudo nmap -sn 192.168.2.0/24
```

- `-sN` - No port scan (aka ping scan)

After identifying all alive host you can then start doing port scanning.

[[netdiscover]] is an equivalent to `nmap`, but utilizes ARP requests:

```bash
sudo netdiscover -i eth0 -r 192.168.2.0/24
```
