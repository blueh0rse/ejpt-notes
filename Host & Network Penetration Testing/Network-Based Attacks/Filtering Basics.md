---
up: "[[Network-Based Attacks]]"
tools:
  - "[[Tshark]]"
---

# Filtering Basics

```bash
# read a pcap file
tshark -r <file> 
# filters example
tshark -r <file> -Y 'http'
tshark -r <file> -Y 'ip.src==<ip> && ip.dst==<ip>'
tshark -r <file> -Y 'http contains password'
```
