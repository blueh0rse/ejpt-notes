---
up: "[[Networking Primer]]"
---

# Network Layer

- Responsible for logical addressing, routing and forwarding data packets between devices across different networks
- Determine optimal path for data to travel from source to destination

## Protocols

- IP - Internet Protocol
	- Central protocol part of the foundation of the Internet
	- IPv4 - employs 32-bits addresses represented as four sets of octets separated by dots.
	- IPv6
	- Logical Addressing
	- Packet Structure
	- Fragmentation and Reassembly
	- IP Addressing Types
		- unicast
		- broadcast
		- multicast
	- Subnetting
- ICMP - Internet Control Message Protocol
	- Used for error reporting and diagnostics
	- ICMP messages include `ping`, `traceroute` and various error messages
- DHCP
	- Dynamically assign IP addresses to devices on a network

## Reserved IPv4 Addresses

- `0.0.0.0` - `0.255.255.255` represents "this" network
- `127.0.0.0` - `127.255.255.255` represents the local host
- `192.168.0.0` - `192.168.255.255` is reserved for private networks
- More details in the [[RFC5735]]
