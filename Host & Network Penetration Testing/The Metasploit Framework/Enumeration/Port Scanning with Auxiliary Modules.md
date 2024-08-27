---
up: "[[4. ARCHIVES/eJPTv2/Host & Network Penetration Testing/The Metasploit Framework/Enumeration/Enumeration|Enumeration]]"
---

# Port Scanning with Auxiliary Modules

## Auxiliary Modules

- Used to perform scanning, discovery and fuzzing
- Can be used to perform both TCP & UDP port scanning
- Can be used during the information gathering as well as the post exploitation
- Can be used to discover host and perform port scanning on a different network subnet after obtaining initial access on a target system 

## Demonstration

1. Obtain the target ip address

```bash
> search portscan
> use auxiliary/scanner/portscan/tcp
```

> Always check for subnets with `ifconfig`

```bash
> run autoroute -s <subnet_ip>
```
