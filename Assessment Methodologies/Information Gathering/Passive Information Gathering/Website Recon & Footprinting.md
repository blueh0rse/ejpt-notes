---
up: "[[Passive Information Gathering]]"
---

# Website Recon & Footprinting

- DNS lookup:

```bash
host hackersploit.org
```

`host` command display IPv4 and IPv6 addresses for a given website.

If the website has multiple IP addresses it can be because it is behind a firewall or proxy.

- Find any names or email addresses
- Social media links
- Check for `robots.txt` file to see hidden directories
- Check for `sitemap.xml` to see potentially hidden pages, categories, etc...
- Use [[BuiltWith]] or [[Wappalyzer]] Firefox extensions to enumerate web technologies used
- Use `whatweb` to identify web technologies used from the command line:

```bash
whatweb hackersploit.org
```

- Use [[webhttrack]] to download a local copy of a website
	- Useful to analyze source code of website
	- Get better understanding of site organization
