---
up: "[[The Metasploit Framework]]"
---

# Metasploit Fundamentals

## Installing & Configuring

- Standalone package on Linux & Windows
- Various dependencies

### MSF Database

- msfdb is used to keep track of all our data, scan results...
- used PostgreSQL as database server
- also facilitates the import and storage of scan results like nmap and nessus

- Manage the msfdb with:

```bash
sudo msfdb status
sudo msfdb init
```

- Then run it with:

```bash
msfconsole
msf6 > db_status
```

## MSFconsole

- easy to use all in one interface

### MSF Module Variables

- Modules generally require information
- These option can be configured through variables
- It is possible to set local variables or global variables

Typical variables:

- LHOST: attacker ip
- LPORT: attacker port to receive a reverse connection
- RHOST(S): store the target ip(s)
- RPORT: specify which port to target

### Search

Look for specific things:

```bash
msf6 > search cve:2017 type:exploit platform:windows
```

## Workspaces

- Workspaces allow to keep track of hosts, scans and activities
- MSFconsole let you create, manage and switch between multiple workspaces
- All the data is stored in the msfdb

```bash
# check status
> db_status
# help menu
> workspace -h
# show current ws
> workspace
# create ws
> workspace -a <ws>
# change ws
> workspace <ws>
# delete ws
> workspace -d <ws>
# rename ws
> workspace -r <old_name< <new_name>
```
