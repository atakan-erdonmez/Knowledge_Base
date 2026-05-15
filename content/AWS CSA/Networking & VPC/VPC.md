---
created: 2026-03-30T09:43
updated: 2026-05-01T12:18
---
5 VPC in a region (soft limit)
Min size is /28, max /16

Only private IPv4 ranges are allowed
## Subnets
5 IP addresses are reserved in subnets
They are bound to AZ

## Internet Gateway
Allows resource in a VPC to connect to the internet. Scales horizontally and highly available

- One VPC can only be attached to one IGW and vice versa
- IGW don't allow internet access on their own. You should edit route tables as well

## Route Table 
Route tables should be created for IGW to work properly as well as connect to internet with resources

### Bastion Host
When you have a resource in a private IP that has to be access from public, you can use *bastion host*.

It is a specific resource that is in public host, but has direct access to the target resource with a security group and a route.

## NAT Instance (outdated)
Allows resource in private subnets to connect to internet. It should be launched in a public subnet. It is a regular EC2 instance with a specific image
- Must disable EC2 (NAT) setting: source/destination check
- Must have Elastic IP attached to it

It basically acts like a proxy in your own network. You connect to the NAT instance from private network, and server only sees your NAT instances' IP

## NAT Gateway
Fully managed, high availability, higher bandwidth NAT solution. Pay per hour and bandwidth.

- NATGW is created in AZ, uses Elastic IP. Can't be used by EC2 instance in same subnet
- Requires IGW (Private subnet => NATGW => IGW)
- 5 Gbps of bandwidth, auto scale up to 100 Gbps
- No security groups required

#### High Availability
It is resilient in a single AZ, but must create multiple gateways in multi AZ for fault-tolerance

#### NAT Gateway vs NAT Instance
![[NAT differences.png]]


## Egress-only Internet Gateway
*Used for IPv6 only*

Similar to NAT Gateway but for IPv6. It allows your IPv6 instances connect to internet, but blocks access *from* the internet.
- You must update Route Tables

Normally, an instance in a private subnet needs to connect to NAT gateway > Internet GW. If it uses IPv6, it connects to Egress-only IGW without the NATGW

## Notes
- In a VPC, **all subnets are connected by a hidden, implicit router.**