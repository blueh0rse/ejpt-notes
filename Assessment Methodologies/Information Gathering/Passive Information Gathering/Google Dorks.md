---
up: "[[Passive Information Gathering]]"
---

# Google Dorks

How to use Google hack to find pertinent information about a target:

- subdomains
- files
- ...

Limit all results to a specific site (and potentially subdomains):

```dorks
site:ine.com
```

Look for specific results in url:

```dorks
site:ine inurl:admin
```

Enumerate subdomains for a particular site:

```dorks
site:*.ine.com
```

```dorks
site:*.ine.com intitle:admin
```

```dorks
site:*.ine.com filetype:pdf
```

Directory listing enabled:

```dorks
intitle:index of
```

Find an old version of a website:

```dorks
cache:ine.com
```

Also look in [[WayBackMachine]].

Find sites with password

```bash
inurl:auth_user_file.txt
inurl:passwd.txt
```

Great resource is the [[Google Hacking Database]].
