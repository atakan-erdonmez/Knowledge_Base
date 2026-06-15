---
---
Connect two VPC, make them behave like they are in same network.
> Must not have overlapping IP ranges

- Peering is NOT transitive, A-B & B-C connection doesn't mean A-C can connect each other
- You must update route tables in *each VPC's subnets* 
- You can peer different AWS accounts/regions, and can reference a security group instead of IP range