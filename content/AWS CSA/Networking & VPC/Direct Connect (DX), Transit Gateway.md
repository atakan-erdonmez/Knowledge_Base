---
created: 2026-03-30T09:43
updated: 2026-05-06T13:18
---
# Direct Connect (DX)

Dedicated connection from a remote network to your VPC. Requires [[VPN Gateway, Customer Gateway, S2S-VPN#^df075d|Virtual Private Gateway]]. Can access public and private resources

Use cases:
- Increase bandwidth throughput - working w/ large datasets, lower costs
- More consistent network, for real-time data feeds
- Hybrid environments (on-prem & cloud)

You need a physical location of AWS. Then, you rent a customer or partner router as well as Direct Connect Endpoint, tunneling to your VPC.


## Direct Connect Gateway
After establishing a DX, you can use a DX Gateway to access more VPC on different regions


# Transit Gateway
It is for peering for thousands of VPC and on-premises connections. You connect network resources like VPCs, VPN Connections, Direct Connect etc and everything will be able to access everything, no manual peering required.

- Supports cross account and cross region
- Supports IP Multicast (not supported by any other AWS service)
- Route tables: limit which VPC can talk with other VPC
### S2S VPN with ECMP
ECMP: Equal-cost multi-path routing

It means creating multiple best-paths. You can use Transit Gateway to create multiple S2S connections from your data center, using one or more Virtual Private Gateway, which increases bandwidth