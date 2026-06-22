[[DNS Zone Apex Record]], [[DNS CNAME, Alias, A Records]]

### 1. The "CNAME Exclusivity" Rule

According to the DNS specification, if a CNAME record is present at a specific name, **no other record types can exist for that same name.** A CNAME tells the resolver: _"Everything you need to know about this name is actually located over at this other name."_ Because of this, a DNS server cannot process a CNAME alongside any other record for the exact same hostname.

### 2. The Apex Requires Other Records

The zone apex (the root domain, like `example.com`) **must** contain other records to function properly:

- **SOA (Start of Authority):** Defines core administrative data about the DNS zone.
- **NS (Name Server) Records:** Directs traffic to the authoritative DNS servers hosting the zone.


If you place a CNAME at `example.com`, the exclusivity rule kicks in and effectively "blots out" your mandatory SOA and NS records. This breaks the DNS zone completely, which is why standard DNS servers will reject a CNAME at the apex.

## Why You Can Use Alias Records

An **Alias record** is not an official DNS record type defined in the original RFCs; it is a smart, server-side workaround created by modern DNS providers (like AWS [[Route 53]], Cloudflare, or Azure DNS).

Here is how it bypasses the apex limitation:

- **It mimics an A record to the outside world:** When a DNS client asks for `example.com`, the DNS provider's nameserver catches the request, looks at the target hostname defined in the Alias (e.g., a load balancer URL), resolves that hostname to its current IP addresses internally, and answers the client with a standard **A record (IP address)** response.
    
- **It avoids the exclusivity conflict:** Because the DNS server serves a clean IP address to the outside world instead of a pointer redirect, it does not violate the CNAME exclusivity rule. The mandatory SOA and NS records at the apex remain completely unaffected and valid.
    

In short: A CNAME forces the _client's browser_ to do the extra work of resolving the next hostname, while an Alias record makes the _DNS provider's nameserver_ do that work behind the scenes, allowing it to present itself as a standard apex-friendly A record.