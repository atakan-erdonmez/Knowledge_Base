---
created: 2026-03-30T09:43
updated: 2026-05-06T13:29
---
To connect Site-to-Site VPN, you need:
1. Virtual Private Gateway (VGW) ^df075d
	- VPN concentrator on the AWS side
	- VGW is created and attached to the VPC 

2. Customer Gateway (CGW)
	- Software application or physical device on datacenter side

> Important step: You should enable **Route Propagation** 


### VPN CloudHub
For multiple VPN connections. Low-cost hub-and-spoke model.

