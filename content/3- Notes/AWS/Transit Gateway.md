---
link:
  - "[[VPC]]"
tag:
  - "[[00_KnowledgeBase/2- Tags/Networking|Networking]]"
---
[[VPN Gateway, Customer Gateway, S2S-VPN]]
# Transit Gateway
It is for peering for thousands of [[VPC]] and **on-premises** connections. You connect network resources like:
- VPCs
- VPN Connections
- [[Transit Gateway|Direct Connect]]
- Transit Gateway peering connections
and everything will be able to access everything, no manual peering required.


- Supports cross account and cross region
- Supports IP Multicast (not supported by any other AWS service)
- Route tables: limit which VPC can talk with other VPC, use **route propagation** for automatic routing with each new VPC
- Use **Transit Virtual Interface (VIF)** with Direct Connect for on-prem to AWS connection

### What is a VIF (Virtual Interface)?

When you get an AWS Direct Connect (DX) link, it is just a physical fiber-optic cable connecting your router to AWS's router inside a data center. By itself, that physical wire doesn't route traffic.

A **Virtual Interface (VIF)** is a VLAN (Virtual LAN) that you configure on top of that physical Direct Connect link to allow data to flow. It dictates _where_ your on-premises traffic is allowed to go once it hits the AWS side.

AWS provides three distinct types of VIFs depending on your destination target:

#### 1. Public VIF (The Correct Answer)

A Public VIF allows your on-premises data center to directly connect to **public AWS services** using AWS public IP addresses, without going over the public internet.

- **Target Services:** Amazon S3, DynamoDB, Amazon SQS, public EC2 endpoints, or AWS API endpoints.

- **How it works:** AWS advertises all its global public IP address ranges over this BGP session to your on-premises router. Your traffic goes straight from your data center, down the Direct Connect wire, and lands directly on S3's public endpoints inside the AWS network.

#### 2. Private VIF

A Private VIF connects your on-premises data center directly to your private resources inside a **VPC**.

- **Target Services:** EC2 instances, RDS databases, internal load balancers, or anything using a private RFC 1918 IP address (e.g., `10.0.0.0/8`).

- It cannot natively talk to public services like Amazon S3 unless you introduce extra routing infrastructure inside a VPC (like an S3 Interface Endpoint/PrivateLink).
#### 3. Transit VIF

A Transit VIF is a special type of VIF used exclusively to connect your physical Direct Connect link to an **AWS Transit Gateway**. From there, the Transit Gateway routes your traffic to hundreds of different VPCs. 


### S2S VPN with ECMP
ECMP: Equal-cost multi-path routing

It means creating multiple best-paths. You can use Transit Gateway to create multiple S2S connections from your data center, using one or more Virtual Private Gateway, which increases bandwidth


**Explanation**

A single AWS Site-to-Site VPN tunnel has a maximum strict throughput limit of **1.25 Gbps**. Even if your on-premises internet connection is 10 Gbps, a single VPN connection (which consists of two tunnels for high availability, but only uses one actively for traffic by default) cannot exceed this 1.25 Gbps ceiling.

To bypass this limitation and maximize throughput, you must scale horizontally using **Equal-Cost Multi-Path (ECMP)** routing over **AWS Transit Gateway (TGW)**:

- **How it works:** When you terminate your Site-to-Site VPN connections into an AWS Transit Gateway (instead of a standard Virtual Private Gateway), you can enable ECMP.

- **Aggregation:** ECMP allows the Transit Gateway to distribute traffic simultaneously across multiple active VPN tunnels. By establishing multiple VPN connections and leveraging both tunnels per connection, AWS aggregates the bandwidth. For example, using 4 active tunnels with ECMP boosts your aggregate throughput up to **5 Gbps** ($4 \times 1.25\text{ Gbps}$).