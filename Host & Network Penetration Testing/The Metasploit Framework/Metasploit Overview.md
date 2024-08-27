---
up: "[[The Metasploit Framework]]"
tools:
  - "[[Metasploit]]"
---

# Metasploit Overview

## What is the Metasploit Framework?

- Open source robust pentest and exploitation framework
- One of the largest database of public, tested exploits
- Robust infrastructure required to automate every stage of a pentest
- Used to develop and test exploits
- Designed to be modular allowing for new functionality to be implemented
- Source code is available in Github

### History

- Developed by HD Moore in 2003
- Originally developed in Perl
- Rewritten in Ruby in 2007
- Acquired by Rapid7 in 2009
- v5.0 in 2019
- v6.0 in 2020

### Terminology

- Interface: methods of interaction
- Module: piece of code that performs a particular task
- Vulnerability: weakness or flaw in a host or a network
- Exploit: piece of code/module used to take advantage a vulnerability
- Payload: piece of code delivered to the target system by an exploit
- Listener: utility listening for an incoming connection from a target

- MSF Console is an interface that provides you access to all the functionality of the framework
- MSF CLI is used to facilitate the creation of automation scripts that utilize modules. discontinued in 2015.
- MSF Community Edition is a web based GUI front-end
- Armitage is a free Java based GUI front-end for MSF

## Architecture

![[Pasted image 20240221223426.png]]

- a module is a piece of code that can be used by MSF
- the libraries facilitate the execution of modules without having to write the code to execute them

### Modules

- Exploit: a module that is used to take advantages of vulnerability and is typically paired with a payload
- Payload: code that is delivered by MSF and remotely executed on the target after successful exploitation.
	- Example: a reverse shell that initiates a connection from the target to our system
- Encoder: used to encode payloads in order to avoid AV detection
	- Example: `shikata_ga_na`i is used to encode Windows payloads
- NOPS: used to ensure that payloads sizes are consistent and ensure the stability of a payload when executed
- Auxiliary: a module that is used to perform additional functionality like port scanning and enumeration. Cannot be paired with a payload.

### Payloads

2 types of payload:

1. Non-staged payload: sent to the target as is along with the exploit
2. Staged payload: sent to the target in two parts:
	- first part (stager) contains a payload used to establish a reverse connection back to the attacker, download the second part of the payload (stage) and execute it.

#### Stagers and Stages

1. Stagers are typically used to establish a stable communication channel between the attacker and the target after which a stage payload is downloaded and executed on the target system
2. Stage are payload components that are downloaded by the stager

#### Meterpreter payload

- Meta-Interpreter: advanced multi-function payload that is executed in memory on the target system making it difficult to detect
- Communicates over a stager socket and provides and interactive command interpreter on the target system

## MSF File System Structure

- Module locations: `/usr/share/metasploit-framework/modules`
- User specified modules are stored under: `~/.ms4/modules`

## Pentest with MSF

- used to perform and automate various tasks of a pentest life cycle
- Penetration Testing Execution Standard (PTES)

| Pentest Phase | MSF Implementation |
| ---- | ---- |
| Information Gathering & Enumeration | Auxiliary Modules |
| Vulnerability Scanning | Auxiliary Modules & Nessus |
| Exploitation | Exploit Modules & Payloads |
| Post Exploitation | Meterpreter |
| Privilege Escalation | Post Exploitation Modules & Meterpreter |
| Persistence | Post Exploitation Modules & Persistence |
