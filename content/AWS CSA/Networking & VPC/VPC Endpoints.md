---
link:
  - "[[VPC]]"
---
Uses PrivateLink

Every AWS service is publicly exposed. [[VPC]] Endpoints allows you to connect to AWS services using a private network, without using internet. 


---
A **VPC endpoint** allows you to privately connect your VPC to supported AWS and VPC endpoint services powered by AWS PrivateLink without needing an Internet gateway, NAT computer, VPN connection, or AWS Direct Connect connection. Instances in your VPC do not require public IP addresses to communicate with resources in the service. Traffic between your VPC and the other service does not leave the Amazon network.

---


#### Interface Endpoint
It is essentially a virtual network card with a private IP address from your subnet's IP range. It acts as an entry point for traffic destined for a specific service. It is more expensive than Gateway Endpoint.

You get billed for the time endpoint is running and the data it processed. More expensive.

#### Gateway Endpoint (preferred)
It is a target in your VPC Route Table used to reach specific AWS services. It does not use an IP address or a network interface.

When you create one, you select which Route Tables should be updated. AWS then adds a route that directs traffic for that service through the gateway.

Cheaper, since it doesn't incur cost for in-region data transfer.

It only supports:
- [[S3]]
- [[DynamoDB]]