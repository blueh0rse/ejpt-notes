---
up: "[[Network-Based Attacks]]"
---

# Filtering Wifi

```bash
tshark -r <file> -Y 'wlan.fc.type_subtype=0x000c'
tshark -r <file> -Y 'eapol '
```
