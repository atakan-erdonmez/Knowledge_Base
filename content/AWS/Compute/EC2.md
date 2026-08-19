---
link:
  - "[[AWS]]"
tag:
  - "[[Compute]]"
---
Elastic Compute Cloud = Infrastructure as a Service
Capabilities:
- Renting virtual machines (EC2)
- Storing data on virtual drives ([[EBS (Elastic Block Store)]])
- Distributing load across machines ([[Elastic Load Balancer (ELB)|Elastic Load Balancer (ELB)]])
- Scaling the service using an auto-scaling group ([[Auto Scaling Groups (ASG)]])



**Note**: When rebooting an instance, public IP renews.

# Security Groups
Fundamental of network security. They control how traffic is allows into or out of EC2


# Instance Store
High-performance hardware disk that is temporary.
- Better I/O performance
- Lose their storage if EC2 instance is stopped (**ephemeral**)
- Good for buffer / cache / scratch data / temporary content
- Risk of data loss if hardware fail

It is a low cost, good random I/O option for data that is temporary like cache, or copied across a fleet.

-  When you stop, hibernate, or terminate an instance, every block of storage in the instance store is reset.
- You can specify instance store volumes for an instance only when you launch it.
- If you create an Amazon Machine Image (AMI) from an instance, the data on its instance store volumes isn't preserved
- You can't detach an instance store volume from one instance and attach it to a different instance
# Tenancy
It means the underlying hardware usage. You can have shared (default), dedicated instance, and dedicated hosts. The VPC default setting is also important as well as launch template.

> Note: Dedicated always wins against shared.


---
# Index
```dataview
LIST
FROM ""
WHERE contains(link, [[EC2]])
```
