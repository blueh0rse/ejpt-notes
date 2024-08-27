---
up: "[[Active Information Gathering]]"
---

# DNS Zone Transfers

Domain Name System (DNS) is a protocol that is used to resolve domain names/hostnames to IP addresses.

## DNS Records

- `A` - Hostname/domain IPv4 address
- `AAAA` - Hostname/domain IPv6 address
- `NS` - Domains nameserver
- `MX` - Domain mail server
- `CNAME` - Domain aliases
- `TXT` - Text
- `HINFO` - Host information
- `SOA` - Domain authority
- `SRV` - Service
- `PTR` - IP to hostname

## DNS interrogation

- Process of enumerating DNS records for a specific domain
- The objective is to probe a DNS server to provide us information about a specific domain
- Can provide important information like IP address, subdomains, mail server...

## DNS Zone Transfer

- Zone Transfer: when admins want to copy or transfer zone files from one DNS server to another
- If misconfigured can be abused to copy the zone file from primary DNS server to another DNS server
- A DNS Zone Transfer can provide pentesters with a holistic view of an organization's network layout or even provide internal network addresses

 [[dnsenum]] can be used to do passive, active information gathering and DNS zone transfer.

```bash
dnsenum zonetransfer.me
```

`/etc/hosts` file can be used to map an IP address to a custom hostname.

[[dig]] is another DNS lookup utility.

```bash
dig axfr @subdomain zonetransfer.me
```

[[fierce]] is a scanner looking for IP addresses against a specified domains.

```bash
fierce -dns zonetransfer.me
```
