---
link:
  - "[[VPC]]"
---
# Flow Logs
Capture info about IP traffic: VPC, subnet, ENI.

- Data can go to S3, CloudWatch Logs, and Kinesis Data Firehose.
- Capture from AWS managed interfaces: ELB, RDS, ElastiCache, Redshift, WorkSpaces, NATGW, Transit Gateway...

#### Syntax

![[VPC flow log syntax.png]]

> A common exam scenario asks how to troubleshoot why an instance can't reach the internet:
- If Flow Logs show **REJECT**, it's a **Security Group** or **NACL** issue.
- If Flow Logs show **nothing** (no record at all), it’s likely a **Routing** issue (check the Route Table/Internet Gateway).
