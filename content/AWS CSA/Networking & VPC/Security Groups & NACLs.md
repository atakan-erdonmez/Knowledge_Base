---
created: 2026-03-30T09:43
updated: 2026-05-06T13:18
---
NACLs (Network ACLs) sit before the subnet. They check the connection to the EC2 instance even before security group, before it hits the subnet. If it allows, then it goes to the security group.

- NACLs -> stateless (outbound rules matter, it might not allow exiting traffic even though it was accepted when entering)
- Security groups -> stateful (anything accepted in will go out without any further check, outbound checks don't matter)

# NACLs
They are like a firewall which control traffic *to and from subnets*. One NACL per subnet, new subnets are assigned Default NACL.

NACL rules:
- Has a number 1-32766, lower number = higher priority. Match first
- Newly created NACLs will deny everything

### Default NACL
Accepts everything inbound/outbound with the subnets it's associated with

### Ephemeral Ports
When client is connecting to a service, client opens a temporary port for the response, called ephemeral port
> Stateful firewalls follow these by *established* and *related* statuses

## Security Group vs NACL
![[security group vs nacl.png]]