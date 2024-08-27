---
up: "[[Host Discovery]]"
---

# Host Discovery Techniques

- Crucial phase to identify live hosts on a network

## Techniques

- Ping Sweeps (ICMP Echo Requests), quick and commonly used method
	- Windows firewall blocks it by default
- ARP Scanning: Using ARP requests to identify hosts on a local network
	- Needs to be connected to a network to scan it
- TCP SYN Ping (Half-Open Scan): Send to a specific port to check if a host is alive
	- Stealthier than ICMP requests
- UDP Pings: effective for hosts that do not respond to ICMP or TCP probes
- TCP ACK Ping: expect no response but if a TCP RST is received it indicates the host is alive
- SYN ACK Ping: same as TCP ACK

- The choice depends on various factors:
- ICMP Ping:
	- Widely supported
	- Easily detected, some firewalls block it by default
- TCP SYN Ping:
	- stealthier than ICMP and may bypass firewalls that allows outbound connections
	- some hosts may not respond
