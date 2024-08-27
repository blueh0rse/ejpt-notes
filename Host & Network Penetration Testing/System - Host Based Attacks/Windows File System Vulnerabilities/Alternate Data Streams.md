---
up: "[[Windows File System Vulnerabilities]]"
---

# Alternate Data Streams

- ADS is an NTFS (New Technology File System) file attribute
- Was designed to provide compatibility with the MacOS HFS (Hierarchical File System)
- Any file created on an NTFS formatted drive will have 2 different forks/streams:
	- Data stream: Default stream, contains the file data
	- Resource stream: Typically contains file metadata
- Hackers can use ADS to hide malicious code or executables to evade detection
- Can be done by storing the malicious code in the file attribute resource stream of a legitimate file
- Used to evade basic signature based AVs and static scanning tools

## Demonstration

File properties are the file resource stream.

The following command will hide a file inside the resource stream of another file:

```bash
notepad file.txt:secret.txt
```

How to hide a malicious payload to a normal file then make a symbolic link:

```bash
>type payload.exe > windowslog.txt:winpeas.exe
>start windowslog.txt:winpeas.exe
>mklink wupdate.exe C:\Temp\windowslog.txt:winpeas.exe
```
