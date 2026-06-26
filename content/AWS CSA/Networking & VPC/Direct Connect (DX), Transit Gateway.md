---
link:
  - "[[AWS]]"
  - "[[00_KnowledgeBase/Networking/Networking|Networking]]"
---
# Direct Connect (DX)

Dedicated connection from a remote network to your VPC. Requires [[VPN Gateway, Customer Gateway, S2S-VPN#^df075d|Virtual Private Gateway]]. Can access public and private resources

It establishes a dedicated, physical network connection from your on-premises data center or co-location facility directly to AWS, bypassing the public internet entirely to provide consistent bandwidth and low latency. Takes **weeks to months** to install.

Use cases:
- Increase bandwidth throughput - working w/ large datasets, lower costs
- More consistent network, for real-time data feeds
- Hybrid environments (on-prem & cloud)

You need a physical location of AWS. Then, you rent a customer or partner router as well as Direct Connect Endpoint, tunneling to your VPC.

> It is not encrypted, you need to use **VPN** for encrypted comunication.

## Direct Connect Gateway
After establishing a DX, you can use a DX Gateway to access more VPC on different regions


# Transit Gateway
It is for peering for thousands of [[VPC]] and **on-premises** connections. You connect network resources like:
- VPCs
- VPN Connections
- [[Direct Connect (DX), Transit Gateway|Direct Connect]]
- Transit Gateway peering connections
and everything will be able to access everything, no manual peering required.


- Supports cross account and cross region
- Supports IP Multicast (not supported by any other AWS service)
- Route tables: limit which VPC can talk with other VPC, use **route propagation** for automatic routing with each new VPC
- Use **Transit Virtual Interface (VIF)** with Direct Connect for on-prem to AWS connection
### S2S VPN with ECMP
ECMP: Equal-cost multi-path routing

It means creating multiple best-paths. You can use Transit Gateway to create multiple S2S connections from your data center, using one or more Virtual Private Gateway, which increases bandwidth


**Explanation**

A single AWS Site-to-Site VPN tunnel has a maximum strict throughput limit of **1.25 Gbps**. Even if your on-premises internet connection is 10 Gbps, a single VPN connection (which consists of two tunnels for high availability, but only uses one actively for traffic by default) cannot exceed this 1.25 Gbps ceiling.

To bypass this limitation and maximize throughput, you must scale horizontally using **Equal-Cost Multi-Path (ECMP)** routing over **AWS Transit Gateway (TGW)**:

- **How it works:** When you terminate your Site-to-Site VPN connections into an AWS Transit Gateway (instead of a standard Virtual Private Gateway), you can enable ECMP.

- **Aggregation:** ECMP allows the Transit Gateway to distribute traffic simultaneously across multiple active VPN tunnels. By establishing multiple VPN connections and leveraging both tunnels per connection, AWS aggregates the bandwidth. For example, using 4 active tunnels with ECMP boosts your aggregate throughput up to **5 Gbps** ($4 \times 1.25\text{ Gbps}$).