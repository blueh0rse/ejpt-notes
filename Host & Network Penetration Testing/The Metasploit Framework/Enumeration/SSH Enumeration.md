---
up: "[[4. ARCHIVES/eJPTv2/Host & Network Penetration Testing/The Metasploit Framework/Enumeration/Enumeration|Enumeration]]"
---

# SSH Enumeration

- We can utilize auxiliary modules to enumerate the version of SSH running on the target as well as perform brute-force attacks to identify passwords

## Demonstration

1. Identify target ip
2. Create workspace
3. Set global RHOSTS
4. use auxiliary/scanner/ssh/ssh_version
5. use auxiliary/scanner/ssh/ssh_login
	1. set user_file
	2. set user_pass
6. use auxiliary/scanner/ssh/ssh_enumusers
	1. set user_file
