---
created: 2026-06-14T13:06
updated: 2026-06-14T13:06
---
Every AWS service is publicly exposed. VPC Endpoints allows you to connect to AWS services using a private network, without using internet. 

#### Interface Endpoint
It is essentially a virtual network card with a private IP address from your subnet's IP range. It acts as an entry point for traffic destined for a specific service.

#### Gateway Endpoint (preferred)
It is a target in your VPC Route Table used to reach specific AWS services. It does not use an IP address or a network interface.

When you create one, you select which Route Tables should be updated. AWS then adds a route that directs traffic for that service through the gateway.
