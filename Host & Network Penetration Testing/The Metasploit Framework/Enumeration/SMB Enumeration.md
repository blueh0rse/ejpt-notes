---
up: "[[4. ARCHIVES/eJPTv2/Host & Network Penetration Testing/The Metasploit Framework/Enumeration/Enumeration|Enumeration]]"
---

# SMB Enumeration

- Identify target ip
- Start postgresql service
- start msfconsole
- create workspace
- ``setg RHOSTS <ip>``
- search type:auxiliary name:smb
- use auxiliary/scanner/smb/smb_version
- use auxiliary/scanner/smb/smb_enumusers
- use auxiliary/scanner/smb/smb_enumshares
- use auxiliary/scanner/smb/smb_login
- set smbuser admin
- set pass_file unix_passwords.txt
