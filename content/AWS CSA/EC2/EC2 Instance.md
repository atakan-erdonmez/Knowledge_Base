---
---
Elastic Compute Cloud = Infrastructure as a Service
Capabilities:
- Renting virtual machines (EC2)
- Storing data on virtual drives (EBS)
- Distributing load across machines (ELB)
- Scaling the service using an auto-scaling group (ASG)



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
