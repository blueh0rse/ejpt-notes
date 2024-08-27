---
up: "[[System - Host Based Attacks]]"
---

# Windows Vulnerabilities

## Overview

- Dominant OS worldwide with a market of >70%
- Because it is used by everyone it is more likely to be targeted
- Windows had some severe vulnerabilities
	- Conflicker
	- EternalBlue
- Most of these vulnerability have publicly accessible exploit
- Windows has various OS versions and releases which fragments the threat surface
- Windows was developed in C
- By default Windows is not secure
- Newly discovered vulnerabilities are not immediately patched by Microsoft

- Frequent releases of Windows is also a contributing factor to exploitation
- Windows is also vulnerable to cross platform vulnerabilities (ex: sqli)
- Windows devices are also vulnerable to physical attacks

### Types of Vulnerabilities

- Information disclosure
	- Allows to access confidential data
- Buffer overflows
	- Write data to a buffer and overrun the allocated buffer
- Remote code execution
- Privilege escalation
- Denial of Service (DoS)

## Frequently Exploited Windows Services

- Windows has various natives services and protocols
- They provide an attacker with an access vector
- Having a good understanding of what these services are is a vitally important skill

| Protocol/Service | Port(s) | Purpose |
| ---- | ---- | ---- |
| Microsoft IIS | TCP 80/443 | Proprietary web server software |
| WebDAV | TCP 80/443 | HTTP extension that allows clients to update, delete, move and copy files on a web server. It is used to enable a web server to act as a file server |
| SMB/CIFS | TCP 445 | Network file sharing protocol that is used to facilitate the sharing of files between computers on a local network |
| RDP | TCP 3389 | Proprietary GUI remote access protocol developed by Microsoft and is used to remotely authenticate and interact with a Windows system |
| WinRM | TCP 5986/443 | Windows remote management protocol that can be used to facilitate remote access with Windows systems |
