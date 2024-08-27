---
up: "[[Networking Primer]]"
---

# Transport Layer

- 4th layer of the OSI model
- It facilitates communication between 2 devices on a network

## Protocols

- TCP - Transmission Control Protocol
	- Connection-oriented protocol
	- Reliable and ordered delivery of data
	- 3-way handshake
		- -> SYN
		- <- SYN-ACK
		- -> ACK
- UDP
	- Connectionless protocol
	- faster but provides no guarantees of reliability
	- Used for real-time application
		- audio & video streaming
		- online gaming
		- VoIP

### TCP Port Range

- Well-know ports (0-1023)
	- Reserved for standardized services and protocols
	- 80 - HTTP
	- 443 - HTTPS
	- 21 - FTP
	- 22 - SSH
	- 25 - SMTP
	- 110 - POP3
- Registered ports (1024-49151)
	- Registered for specific services or applications
	- But they are not standardized
	- 3389 - RDP
	- 3306 - MySQL
	- 8080 - HTTP alternative
	- 27017 - MongoDB

See active TCP connections:

```bash
netstat -antp
```
