---
link:
  - "[[DynamoDB]]"
---
## Features
### DynamoDB Accelerator (DAX)
Fully-managed, highly available, seamless in-memory cache. Help solve read congestion, *microsecond latency*. Doesn't require application logic modification. TTL=5 min by default

### Stream Processing
Ordered stream of item-level modifications (create/update/delete) in a table. Necessary for *Global Tables*
Use cases:
- React to changes in real time (welcome email to users)
- Real-time usage analytics
- Insert into derivative tables
- Implement cross-region replication
- Invoke AWS [[Lambda]] on changes to you DynamoDB


### Global Tables
It means that tables that are global will have two-way replication. This makes DynamoDB table accessible with low latency in multiple regions. 
- Active-Active replication
- Multi-region **multi-writer**
- Applications can read and write to the table in any region
- Must enable DynamoDB Streams as a pre-requisite

### TTL
Automatically delete items after an expiry timestamp

### Backups

**Continuous backups using point-in-time recovery (PITR)**
- Optionally enabled for last 35 days
- Point-in-time recovery to any time within backup windows
	- Backup creates a new table 

**On-demand backups**
- Full backups for long-term retention, until explicitly deleted
- Doesn't affect performance or latency
- Can be configured with AWS Backup (enable cross-region copy)
- Recovery creates a new table

### Deletion Protection
It prevents accidental table deletion.
### [[S3]] Integration
**Export to S3 (with PITR)**
- Works for any point-of-time in last 35 days
- No affect on read capacity
- Retain snapshots, perform data analysis
**Import from S3**
- Import CSV, DynamoDB JSON or ION format
- No affect on write capacity
- Creates a new table

### [[AppSync]] Integration
You can also use AppSync with DynamoDB to make it easy for you to build collaborative apps that keep shared data updated in real-time. You just specify the data for your app with simple code statements, and AWS AppSync manages everything needed to keep the app data updated in real-time. This will allow your app to access data in Amazon DynamoDB, trigger AWS Lambda functions, or run Amazon OpenSearch Service queries and combine data from these services to provide the exact data you need for your app.