---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
tag:
  - "[[00_KnowledgeBase/2- Tags/Networking|Networking]]"
---

Dedicated connection from a remote network to your VPC. Requires [[VPN Gateway, Customer Gateway, S2S-VPN#^df075d|Virtual Private Gateway]]. Can access public and private resources

It establishes a dedicated, physical network connection from your on-premises data center or co-location facility directly to AWS, bypassing the public internet entirely to provide consistent bandwidth and low latency. Takes **weeks to months** to install.

Use cases:
- Increase bandwidth throughput - working w/ large datasets, lower costs
- More consistent network, for real-time data feeds
- Hybrid environments (on-prem & cloud)

You need a physical location of AWS. Then, you rent a customer or partner router as well as Direct Connect Endpoint, tunneling to your VPC.

> It is not encrypted, you need to use **VPN** for encrypted comunication.

## Direct Connect Gateway
It allows you to connect DX connections and [[VPC]]s together, enabling **transitive routing**.

A Direct Connect gateway is a global resource that allows VPCs in any AWS Region (except China) to connect to Direct Connect via virtual private gateways (VGWs). By connecting both Direct Connect links to the same DX gateway and associating the VGWs of all relevant VPCs, **the company can enable transitive routing across Regions and between on-premises locations and VPCs** — without setting up complex peering or custom VPN appliances.


