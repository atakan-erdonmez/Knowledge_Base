---
link:
  - "[[AWS]]"
tag:
  - "[[2- Tags/Databases|Databases]]"
---
# Elastic Disaster Recovery (DRS)
Quickly and easily recover your physical, virtual, and cloud-based servers to AWS.

It is a continuous block-level replication for your servers. Copy your data into AWS with EC2 and EBS and failover in minutes with bigger resources on AWS.


# Database Migration Services (DMS)
Quickly and securely migrate to AWS, resilient, self-healing. The source database remains available. No downtime.

Sources can be:
- Oracle, MSSQL, MySQL, Postgresq, MongoDB, Azure, RDS, S3...

Targets can be:
- On premises, [[RDS]], [[Redshift]], [[S3]], Kafka...

>[!note]
>You can migrate data to Amazon S3 using AWS DMS from any of the supported database sources. When using **Amazon S3 as a target** in an AWS DMS task, both full load and change data capture (CDC) data is written to **comma-separated value (.csv) format by default**.

## Use Cases
#### Moving from [[S3]] to [[Kinesis Data Stream]]
*'A Big Data analytics company writes data and log files in Amazon S3 buckets. The company now wants to stream the existing data files as well as any ongoing file updates from Amazon S3 to Amazon Kinesis Data Streams.'*
 
You can achieve this by using AWS Database Migration Service (AWS DMS). AWS DMS enables you to seamlessly migrate data from supported sources to relational databases, data warehouses, streaming platforms, and other data stores in AWS cloud.

>  While DMS was originally built for database-to-database migrations, AWS has expanded its capabilities significantly. In modern cloud architecture, DMS is heavily used as a data replication and ingestion tool for data lakes and streaming pipelines.
# Schema Conversion Tool (SCT)
Convert your database's schema from one engine to another
- SQL to MySQL
- Oracle to Amazon Redshift 