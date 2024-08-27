---
up: "[[4. ARCHIVES/eJPTv2/Host & Network Penetration Testing/The Metasploit Framework/Enumeration/Enumeration|Enumeration]]"
---

# MySQL Enumeration

- We can utilize auxiliary modules to enumerate the MySQL versio used, perform brute-force attacks to identify passwords, execute SQL queries...

## Demonstration

1. Identify target ip address
2. Create workspace
3. Set global variable RHOSTS
4. search type:auxiliary name:mysql
5. use auxiliary/scanner/mysql/mysql_version
6. use auxiliary/scanner/mysql/mysql_login
	1. set username or user_file
	2. set pass_file
7. use auxiliary/admin/mysql/mysql_enum
	1. set password
	2. set username
8. use auxiliary/admin/mysql/mysql_sql
	1. set password
	2. set username
	3. set sql show databases;
	4. ``set sql use <db>``
9. use auxiliary/scanner/mysql/mysql_schema
	1. set username
	2. set password
