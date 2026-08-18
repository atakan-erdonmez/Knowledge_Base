---
link: "[[00_KnowledgeBase/1- MOCs/AWS]]"
tag:
  - "[[00_KnowledgeBase/2- Tags/Networking|Networking]]"
---
## Core Concept

- **What it is:** A secure networking technology that provides private connectivity between VPCs, AWS services, and SaaS applications **without traversing the public internet**.

- **The Mechanism:** Uses encapsulation to map an **Elastic Network Interface (ENI)** with a private IP in a consumer subnet directly to a **Network Load Balancer (NLB)** or **Gateway Load Balancer (GWLB)** in a provider network.


## Key Features

- **Security:** Traffic stays entirely on the AWS global backbone network. No Internet Gateway (IGW), NAT Gateway, or public IPs required.

- **Unidirectional:** Connections are strictly consumer-initiated, eliminating external inbound attack vectors.

- **No IP Conflicts:** Fully supports **overlapping CIDR blocks** between connecting networks (unlike traditional VPC Peering).

- **Granular Control:** Consumer access can be restricted using standard **Security Groups** attached directly to the Interface Endpoint.


## PrivateLink vs. VPC Endpoints

- **PrivateLink** is the underlying technology.

- **[[VPC Endpoints]]** are the actual resources provisioned in a VPC:

	- **Interface Endpoints:** Powered by PrivateLink. Drops an ENI with a private IP into a subnet. Costs an hourly rate + data processing fees. Supports most AWS services and SaaS.
	
	- **Gateway Endpoints:** _Not_ powered by PrivateLink. Acts as a routing target in a VPC route table. **Free of charge**, but exclusively supports **Amazon S3** and **Amazon DynamoDB**.
	

## Primary Use Cases

1. **Consuming Services (Interface Endpoints):** Accessing AWS services or external SaaS platforms (e.g., Snowflake, Datadog) securely via local private IPs.

2. **Sharing Services (VPC Endpoint Services):** Hosting an application behind an NLB and securely sharing/selling it to other AWS accounts via a unique PrivateLink service name.

3. **Security Traffic Inspection (GWLB):** Routing multi-VPC traffic through centralized third-party firewalls and inspection appliances via Gateway Load Balancer Endpoints.