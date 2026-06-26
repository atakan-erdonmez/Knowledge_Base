---
---
Managed extract, transform, and load (ETL) service
- Useful to prepare and transform data for analytics
- Fully serverless service

**Some features**
- **Glue Job Bookmarks**: prevent re-processing old data 
- **Glue DataBrew**: clean and normalize data using pre-built transformation, prepare for analysis and ML
- **Glue Studio**: new GUI to create, run and monitor ETL jobs in Glue
- **Glue Streaming ETL (built on Apache Spark Structured Streaming)**: compatible with Kinesis Data Streaming, Kafka, MSK (managed Kafka)

## Job Bookmarking
One of the features that make AWS Glue especially useful is job bookmarking. Job bookmarking is a mechanism that allows AWS Glue to keep track of where a job is left off in case it gets interrupted or fails for any reason. This way, when the job is restarted, it can pick up from where it left off instead of starting from scratch.

## Crawler
You can use AWS Glue crawlers to automatically infer database and table schema from your data in Amazon [[S3]] and store the associated metadata in the AWS Glue Data Catalog. Athena [[Athena]] the AWS Glue Data Catalog to store and retrieve table metadata for the Amazon S3 data in your AWS account. The table metadata lets the Athena query engine know how to find, read, and process the data that you want to query.