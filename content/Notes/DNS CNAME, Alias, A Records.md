---
tags:
  - dns
  - network
---
[[DNS Zone Apex Record]], [[Why You Can't Use CNAME at the Apex]]

CNAME record is just used for subdomains: 
- `www.example.com -> example.com`
A & AAAA records are just for IP addresses
- `example.com -> 8.8.8.8`

Alias is a middle ground. It is used in certain DNS providers like Cloudflare and [[Route 53]]. 
- It points to a domain name, but unlike CNAME, the DNS provider automatically resolves the target hostname to the underlying A record, like resolving to a [[Application Load Balancer]].

> [!Warning]
> Since you cannot use CNAME records in zone apex, aliases solve this limitation.
