---
up: "[[Host Discovery]]"
---

# Ping Sweeps

- Network scanning technique used to discover live hosts
- Send a series of ICMP Echo Request (`ping`) messages and observe the responses to determine if the host if reachable

- Windows blocks it by default

- Ping sweeps sends a specially crafted ICMP packet (type 8)
- Receives an answer type 0 if host is online/reachable

- No response doesn't mean host is offline:
	- network congestion?
	- temporary unavailability?
	- firewall settings?
- ping is a simple way to know if a host is alive but results must be interpreted according to the network context and host configuration

Send ICMP Echo Request using [[ping]]:

```bash
ping -c 5 10.4.31.111
```

You can also use [[fping]] an improved `ping`:

```bash
fping -a -g 10.10.10.0/24 2>/dev/null
```

- `-a` - shows all alive hosts
- `-g` - generates a target list

- ICMP is not very reliable as there can be Windows host which will look down.
- [[nmap]] can find them by using the `-Pn` flag
