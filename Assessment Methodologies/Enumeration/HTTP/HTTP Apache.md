---
up: "[[HTTP]]"
tools:
  - "[[lynx]]"
---

# HTTP Apache

Linux solution to host websites: Apache.

```bash
nmap <ip> -p 80 -sV
nmap <ip> -p 80 -sV --script banner
```

Using lynx:

```bash
lynx http://<ip>
```

Look for robots.txt file.
