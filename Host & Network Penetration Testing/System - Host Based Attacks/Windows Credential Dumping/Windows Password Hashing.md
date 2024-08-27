---
up: "[[Windows Credential Dumping]]"
---

# Windows Password Hashing

- Windows OS stores hashed user account passwords locally in the SAM (Security Accounts Manager)
- Authentication and verification of user credentials is facilited by the Local Security Authority (LSA)
- Windows versions use 2 different types of hashes
	- LM
		- Disabled since Windows Vista
	- NTLM

## SAM Database

- Database file responsible for managing user accounts and password on Windows
- The SAM database file cannot be copied while the OS is running
- Windows NT kernel keeps the SAM db file locked
	- Attackers typically use in-memory techniques and tools to dump SAM hashes from the LSASS process
- In modern versions of Windows the SAM database is encrypted with a syskey
- Admin privileges are required to access and interact with the LSASS process

## LM (LanMan)

- Default hashing algorithm since NT 4.0
- It is used to hash user passwords
	1. Password is broken into 2x7 character chunks
	2. All characters are then converted into uppercase (not case sensitive)
	3. Each chunk is then hashed separately using DES
- LM hashing is considered weak and does not include salt

![[Pasted image 20240207175350.png]]

## NTLM (NTHash)

- Collection of authentication protocols used to facilitate authentication between computers
- LM hashing was disabled to utilize NTLM hashing
- When a user account is creating it is encrypted using MD4 algorithm
- NTLM improves LM in the following way:
	- Does not split the hash into 2 chunks
	- Case sensitive
	- Allows the use of symbols and unicode characters

![[Pasted image 20240207175842.png]]
