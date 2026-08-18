---
link:
  - "[[VPC]]"
---
| **Feature**          | **🌐 [[VPC Peering]]**                                                         | **🤝 [[VPC Sharing]]**                                                                                      |
| -------------------- | ------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------- |
| **Network Boundary** | Two distinct VPCs with **different** CIDR blocks.                              | One single VPC with **one** CIDR block.                                                                     |
| **IP Address Space** | CIDRs **cannot** overlap.                                                      | Single unified CIDR managed by a central team.                                                              |
| **Management**       | Distributed. Each team manages their own VPC, route tables, and gateways.      | Centralized. An infrastructure team owns the network; subnets are shared out.                               |
| **Transitivity**     | **Non-transitive.** (If A is peered with B, and B with C, A cannot talk to C). | **Naturally Transitive.** All resources in the same subnets can talk by default via standard local routing. |
| **Ideal For**        | Connecting isolated, autonomous environments or legacy systems.                | Multi-tenant applications, microservices, and central enterprise governance.                                |
