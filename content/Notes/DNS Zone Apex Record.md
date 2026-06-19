---
tags:
  - dns
  - network
---
A **DNS zone apex record** (also commonly called a **root domain**, **naked domain**, or **apex domain**) is the base level of your domain name that does not include a subdomain prefix like www.

For example:
- **Zone Apex:** `example.com`
- **Subdomain:** `www.example.com` or `blog.example.com`

### The "Apex" Problem: Why it matters

In standard DNS architecture (defined by RFC 1034), there is a strict technical limitation regarding the zone apex: **The zone apex cannot be a CNAME record.** A CNAME record maps a name to another name (e.g., pointing `www.example.com` to an AWS CloudFront distribution URL). However, a CNAME overrides all other record types for that exact name. Because a zone apex _must_ have other records present to function properly (such as `NS` records for nameservers and `SOA` records for zone authority), assigning a CNAME to the apex would break the domain.

Therefore, under traditional DNS rules, a zone apex can only point directly to an IP address using an **A record** (IPv4) or **AAAA record** (IPv6).

### The Modern Cloud Solution: Alias Records

Because modern cloud infrastructure (like AWS Load Balancers, CloudFront distributions, or S3 buckets) uses dynamic IP addresses that change constantly, you cannot just hardcode an IP address into an A record at the root apex.

To solve this, modern DNS providers invented custom, virtual record types that allow you to route zone apex traffic to cloud resources dynamically:

- **AWS Route 53:** Uses **Alias Records**.
- **Cloudflare:** Uses **CNAME Flattening**.
- **Other Providers:** May call it an **ANAME** or **ALIAS** record.

These special records live at the zone apex but act like a smart A record. When a user requests `example.com`, the DNS provider looks up the current underlying IP address of your cloud resource behind the scenes and responds directly with that IP, bypassing the standard CNAME restriction entirely.