---
created: 2026-03-30T09:43
updated: 2026-05-07T13:00
---
Protect your entire VPC
- From Layer 3 to 7
- Any direction, you can inspect
	- VPC to VPC
	- Ingress, egress
	- Direct Connect, S2S VPN
- Internally, Network firewall uses the AWS Gateway Load Balancer
- Can be managed via [[Shield, WAF & Firewall Manager#Firewall Manager|Firewall Manager]]

 AWS Network Firewall provides some advantages over [[Security Groups & NACLs|NACLs]] alone. NACLs provide only stateless packet filtering, whereas AWS Network Firewall provides **web filtering, intrusion detection and prevention, stateless and stateful packet filtering, and centralized visibility of all your traffic**. 