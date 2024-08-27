---
up: "[[4. ARCHIVES/eJPTv2/Assessment Methodologies/Enumeration/SSH/SSH|SSH]]"
tools:
  - "[[Hydra]]"
---

# SSH - Dictionary Attack

```bash
hydra -l student -P rockyou.txt <ip> ssh
```

```bash
nmap <ip> -p 22 --script ssh-brute --script-args userdb=users.txt
```
