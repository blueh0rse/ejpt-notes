---
up: "[[Passive Information Gathering]]"
---

# WAF with wafw00f

Detecting Web Application Firewall with [[wafw00F]].

Determining the WAF protecting the target website is very useful for the rest of the investigations.

```bash
wafw00f hackersploit.org
```

If no WAF is detected for the website it can potentially means the IP is the IP of the hosting server.

To get more information we will need to wait for the passive information gathering phase.

To test all possible WAF:

```bash
wafw00f https://hackersploit.com -a
```
