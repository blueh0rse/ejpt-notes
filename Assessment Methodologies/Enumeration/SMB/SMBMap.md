---
up: "[[SMB]]"
tools:
  - "[[SMBMap]]"
---

# SMBMap

SMBMap is a python tool to enumerate smb information.

```bash
# anonymous
smbmap -u guest -p "" -d . -H <ip>
```

```bash
# admin user
smbmap -u administrator -p smbserver_771 -H <ip> -x 'ipconfig'
```
