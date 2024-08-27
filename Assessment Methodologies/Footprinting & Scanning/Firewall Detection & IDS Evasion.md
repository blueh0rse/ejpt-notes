---
up: "[[Footprinting & Scanning]]"
---

# Firewall Detection & IDS Evasion

- How to use nmap to detect a filtering system.
- How to modify scans to evade detection systems

- How to detect the presence of a firewall?
	- `-sA`: send ACK packet to open port
		- To know if port if `filtered` or `unfiltered`
- How to evade Firewall/IDS?
	- `-f`: Use packet fragmenting
	- `--mtu 8`: minimum transmission unit
- Gateway IP can be spoofed to trick IDS:
	- Gateway IP is always x.x.x.1
	- `--data-length 200`
	- `-D <gateway ip>`
	- `-g 53`: spoof gateway's source port
