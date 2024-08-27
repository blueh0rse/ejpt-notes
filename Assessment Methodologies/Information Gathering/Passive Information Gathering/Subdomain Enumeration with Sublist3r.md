---
up: "[[Passive Information Gathering]]"
---

# Subdomain Enumeration with Sublist3r

How to passively enumerate subdomains with [[sublist3r]].

No brute-forcing because it is passive information gathering.

Sublist3r is python tool designed to enumerate subdomains using OSINT. It is not 100% accurate as some domains may not be accessible from the internet.

```bash
sublist3r -d hackersploit.com -e google,yahoo -o hackersploit.txt
```

To bypass Google rate limit request it can be good to use a VPN.
