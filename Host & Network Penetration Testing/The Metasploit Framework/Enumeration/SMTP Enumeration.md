---
up: "[[4. ARCHIVES/eJPTv2/Host & Network Penetration Testing/The Metasploit Framework/Enumeration/Enumeration|Enumeration]]"
---

# SMTP Enumeration

- We can utilize auxiliary modules to enumerate the version of SMTP as well as user accounts on the target system

## Demonstration

1. Create workspace
2. Setup global variable RHOSTS
3. Get smtp version 

```bash
use auxiliary/scanner/smtp/smtp_version
```

5. User enumeration

```bash
use auxiliary/scanner/smtp/smtp_enum
```
