---
up: "[[4. ARCHIVES/eJPTv2/Host & Network Penetration Testing/The Metasploit Framework/Enumeration/Enumeration|Enumeration]]"
---

# FTP Enumeration

```bash
> search portscan
> use auxiliary/scanner/portscan/tcp
> set RHOSTS <ip>
# need service version
> search ftp
> search type:auxiliary nmae:ftp
> use auxiliary/scanner/ftp/ftp_version
> search proftpd
# brute force
> use auxiliary/scanner/ftp/ftp_login
> set user_file /usr/share/metasploit-framework/data/wordlists/common_users.txt
> set pass_file /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt
```

When password:

```bash
ftp <ip>
```
