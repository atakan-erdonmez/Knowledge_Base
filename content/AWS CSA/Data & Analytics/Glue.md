---
---
Managed extract, transform, and load (ETL) service
- Useful to prepare and transform data for analytics
- Fully serverless service

**Some features**
- Glue Job Bookmarks: prevent re-processing old data 
- Glue DataBrew: clean and normalize data using pre-built transformation
- Glue Studio: new GUI to create, run and monitor ETL jobs in Glue
- Glue Streaming ETL (built on Apache Spark Structured Streaming): compatible with Kinesis Data Streaming, Kafka, MSK (managed Kafka)

## Job Bookmarking
One of the features that make AWS Glue especially useful is job bookmarking. Job bookmarking is a mechanism that allows AWS Glue to keep track of where a job is left off in case it gets interrupted or fails for any reason. This way, when the job is restarted, it can pick up from where it left off instead of starting from scratch.