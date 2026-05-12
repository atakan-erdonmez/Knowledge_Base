# VPC Peering
Connect two VPC, make them behave like they are in same network.
> Must not have overlapping IP ranges

- Peering is NOT transitive, A-B & B-C connection doesn't mean A-C can connect each other
- You must update route tables in *each VPC's subnets* 
- You can peer different AWS accounts/regions, and can reference a security group instead of IP range

# VPC Endpoints
Every AWS service is publicly exposed. VPC Endpoints allows you to connect to AWS services using a private network, without using internet. 

#### Interface Endpoint
It is essentially a virtual network card with a private IP address from your subnet's IP range. It acts as an entry point for traffic destined for a specific service.

#### Gateway Endpoint (preferred)
It is a target in your VPC Route Table used to reach specific AWS services. It does not use an IP address or a network interface.

When you create one, you select which Route Tables should be updated. AWS then adds a route that directs traffic for that service through the gateway.


# Flow Logs
Capture info about IP traffic: VPC, subnet, ENI.

- Data can go to S3, CloudWatch Logs, and Kinesis Data Firehose.
- Capture from AWS managed interfaces: ELB, RDS, ElastiCache, Redshift, WorkSpaces, NATGW, Transit Gateway...

#### Syntax

![[VPC flow log syntax.png]]

> A common exam scenario asks how to troubleshoot why an instance can't reach the internet:
- If Flow Logs show **REJECT**, it's a **Security Group** or **NACL** issue.
- If Flow Logs show **nothing** (no record at all), it’s likely a **Routing** issue (check the Route Table/Internet Gateway).

# Traffic Mirroring

It mirrors the traffic going to a specific ENI and directs to an ENI or Network LB. This allows reviewing the traffic and examining without interrupting the connection or causing latency