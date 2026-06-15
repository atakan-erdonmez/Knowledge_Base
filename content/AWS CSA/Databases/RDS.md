---
---
- Stands for Relational Database Service
- A managed DB service, use SQL
- It allow to create db that are managed by AWS
	- PostgreSQL
	- MySQL
	- MariaDB
	- Oracle
	- MsSQL
	- IBM DB2
	- Aurora (AWS proprietary)


## Advantages
You can convert an EC2 instance to a database, but what are the advantages of RDS?

RDS is a managed service:
- Automated provisioning, OS patching
	- Continuous backups and restore to specific timestamp (Point in Time Restore)!
	- Monitoring dashboards
	- Read replicas for improved read performance
	- Multi AZ setup for DR (Disaster Recovery)
	- Maintenance windows for upgrades
	- Scaling capability (vertical and horizontal)
	- Storage backed by EBS


> You can’t SSH into your instances

## RDS - Storage Auto Scaling
Dynamic storage increase. RDS detects you are running out of space, and it scales automatically

# Read Replicas
It is the replication for reading purpose. 
- up to 15 read replicas
- Within AZ, cross AZ, cross region
- Replication is ASYNC, reads are consistent
- These replicas can be promoted to their own DB, but requires manual intervention

>[!note]
> In order to encrypt an existing database, you should take a snapshot of the database, copy it as an encrypted snapshot, and then restore a database from the encrypted snapshot.
### Use Cases
On top of an ongoing production database, if you want to run a reporting application to run analytics, it will overrun the database and slow down. Thus, creating a read replica fixes this problem

Note: Read replicas are only used for SELECT statements

### Network Cost
<mark style="background: #FFF3A3A6;">For RDS read replicas within the same region, you don't pay cross AZ or cross-region fee</mark>

# Multi AZ (Disaster Recovery)
It uses SYNC replication
- One DNS name - automatic app failover to standby
- NOT USED FOR SCALING. The backup DB is not used. It activates only when master fails

> [!deneme] Common Exam Questions
> - The Read Replicas can be setup as Multi AZ for Disaster Recovery (DR)
> - To transfer an RDS from Single-AZ to Multi-AZ, you have to click "modify" and chose multi-AZ option. It is a zero downtime operation.


![[multi-az vs read replicas RDS.png]]

# RDS Custom

Managed Oracle and Microsoft SQL Server Database with OS and database customization
- RDS: Automates setup, operation, and scaling of database in AWS
- Custom: access to the underlying database and OS so you can
	- Configure settings
	- Install patches
	- Enable native features
	- Access the underlying EC2 Instance using SSH or SSM Session Manager
- De-activate Automation Mode to perform your customization, better to take a DB snapshot before

- **RDS vs. RDS Custom:**
	- RDS: entire database and the OS to be managed by AWS
	- RDS Custom: full admin access to the underlying OS and the database

# RDS Proxy
Fully managed db proxy for RDS.
- Allows apps to pool and share DB connections to increase efficiency. Reduced RDS & Aurora failover time by up to 66%
- Serverless, autoscaling, highly-available (multi-AZ). Supports RDS and Aurora
- Can do IAM enforcement, requires no code change (mostly), and is never publicly accessible (must be accessed from VPC) [[Lambda]]

# Other
## Database Upgrade
Upgrades to the database engine level require downtime. Even if your Amazon RDS DB instance uses a Multi-AZ deployment, both the primary and standby DB instances are upgraded at the same time. This causes downtime until the upgrade is complete, and the duration of the downtime varies based on the size of your database instance.

## RDS Event Subscription
It is a service that monitors management database events, such as failovers, backups, restarts etc. It doesn't capture database modifications like 'INSERT, DELETE' etc.

You can integrate [[SNS]] for notifications or [[Lambda]] for various functions.

## Enhanced Monitoring
Amazon RDS offers a powerful feature known as **Enhanced Monitoring**, which provides detailed metrics in real-time about the operating system (OS) underlying your database instances. This feature allows users to monitor performance at a granular level through the AWS Management Console or by accessing the Enhanced Monitoring JSON output via CloudWatch Logs. 

By default, these metrics are retained in CloudWatch Logs for 30 days, but this retention period can be adjusted by modifying the retention settings for the `RDSOSMetrics` log group in CloudWatch.