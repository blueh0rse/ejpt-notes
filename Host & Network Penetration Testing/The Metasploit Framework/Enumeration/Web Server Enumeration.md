---
up: "[[4. ARCHIVES/eJPTv2/Host & Network Penetration Testing/The Metasploit Framework/Enumeration/Enumeration|Enumeration]]"
---

# Web Server Enumeration

- We can utilize auxiliary modules to enumerate the web server version, HTTP headers, brute-force directories and much more

## Demonstration

1. Setup workspace
2. Set up global variable
	- RHOSTS
3. use auxiliary/scanner/http/http_version
4. auxiliary/scanner/http/http_header
5. auxiliary/scanner/http/robots.txt
6. auxiliary/scanner/http/dir_scanner
7. auxiliary/scanner/http/file_dir
8. auxiliary/scanner/http/http_login
9. auxiliary/scanner/http/apache_userdir_enum
