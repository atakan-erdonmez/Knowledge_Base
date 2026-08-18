---
link:
  - "[[AWS]]"
tag:
  - "[[Message&Queue]]"
---
![[data firehose.png]]


> Used to be called "Kinesis Data Firehose"

A fully managed service for ETL (extract, transform, load)
- Amazon [[Redshift]] / Amazon [[S3]] / Amazon [[OpenSearch]]
- 3rd party: Splunk / MongoDB / Datadog / NewRelic
- Custom HTTP endpoint

- Automatic scaling, serverless, pay for what you use
- **Near real-time** with buffering capability based on size/time 
- Supports CSV, JSON, Parquet, Avro, Raw Text, Binary data 
- Custom data transformation using Lambda

# [[Kinesis Data Stream]] vs Amazon Data Firehose

| **Feature**         | **Kinesis Data Streams (KDS)**                                                             | **Kinesis Data Firehose (KDF)**                                                                        |
| ------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| **Primary Purpose** | **Ingest and process** streaming data in real-time with custom logic.                      | **Load/Deliver** streaming data directly into storage, data lakes, or analytics tools.                 |
| **Latency**         | **Real-time** (~200 milliseconds).                                                         | **Near-real-time** (minimum 60-second buffer delay).                                                   |
| **Management**      | **Provisioned/On-Demand.** You manage scaling via "Shards" (or use auto-scaling modes).    | **Serverless.** Fully managed, scales automatically up and down with zero administration.              |
| **Data Retention**  | Stores data for 24 hours by default (up to 365 days). Allows multiple apps to replay data. | **No data retention.** It is a pass-through service. Once delivered, the data is gone from the stream. |
| **Destinations**    | Custom consumers (EC2 apps, AWS Lambda, Kinesis Data Analytics).                           | Specific managed destinations ([[S3]], [[Redshift]], [[OpenSearch]], Splunk, HTTP endpoints).          |