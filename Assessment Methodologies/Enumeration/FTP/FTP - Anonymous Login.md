---
up: "[[FTP]]"
---

# FTP - Anonymous Login

```bash
nmap <ip> -p 21 -sV
```

```bash
nmap <ip> -p 21 --script ftp-anon
```

```bash
ftp <ip>
> anonymous
>
ftp> get file.txt
ftp> bye
```
