---
up: "[[FTP]]"
---

# FTP - Basics

File Transfer Protocol: Store file on a server and access it remotely.

```bash
nmap <ip>
```

Port 21 (FTP by default) is open.

```bash
ftp <ip>
```

Try anonymous login (no user, no password)

We can use [[Hydra]] to brute-force users.

```bash
hydra -L common_users.txt -P unix_password.txt <ip> ftp
```

```bash
$ echo "sysadmin" > users.txt
nmap <ip> --script ftp-brute --script-args userdb=users.txt -p 21
```
