---
up: "[[Introduction to Web and HTTP Protocol]]"
---

# Directory Enumeration with Gobuster

```bash
gobuster dir -u <ip> -w common.txt
# to remove code from output:
gobuster dir -u <ip> -w common.txt -b 403,404
# to look for file extention:
gobuster dir -u <ip> -w common.txt .php,.xml,.txt -r
```
