---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
tag:
  - "[[Message&Queue]]"
---
Collet and store streaming data in **real-time**.
![[Kinesis data stream.png]]

- Retention up to 365 days
- Ability to reprocess (replay) data by consumers
- Data can't be deleted from Kinesis (until it expires)
- Data up to 10MiB (typical use cases is a lot of 'small' real-time data)
- Kinesis Producer Library (KPL) to write an optimized producer app
- Kinesis Client Library (KCL) to write an optimized consumer application


> A Kinesis data stream is composed of shards, where each shard stores a sequence of ordered data records. Each record written to the stream is assigned a **unique sequence number**, which allows consumers to process records in the **exact order in which they were received** within a shard. In addition, records are durably stored and replicated across multiple Availability Zones within the same AWS Region, helping ensure that data is not lost even if failures occur.


### Batchf Records
When a host needs to send many records per second (RPS) to Amazon Kinesis, simply calling the basic PutRecord API action in a loop is inadequate. 

To reduce overhead and increase throughput, the application must batch records and implement parallel HTTP requests. This will increase the efficiency overall and ensure you are optimally using the shards.
## Capacity Modes
#### Provisioned mode
- Choose number of **shards** (how much throughput)
- Each shard gets 1MB/s in (or 1000 records per second)
- Each shards get 2MB/s out
- Scale manually to increase or decrease shards
- Pay per shard provisioned per hour
#### On-demand mode
- No need to provision or manage capacity
- Default capacity provisioned (4 MB/s in or 4000 records/s)
- Scales automatically based on observed throughput in last 30 days
- Pay per stream hour & data in/our per GB

# Kinesis Data Stream vs [[Amazon Data Firehose]]

| **Feature**         | **Kinesis Data Streams (KDS)**                                                             | **Kinesis Data Firehose (KDF)**                                                                        |
| ------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| **Primary Purpose** | **Ingest and process** streaming data in real-time with custom logic.                      | **Load/Deliver** streaming data directly into storage, data lakes, or analytics tools.                 |
| **Latency**         | **Real-time** (~200 milliseconds).                                                         | **Near-real-time** (minimum 60-second buffer delay).                                                   |
| **Management**      | **Provisioned/On-Demand.** You manage scaling via "Shards" (or use auto-scaling modes).    | **Serverless.** Fully managed, scales automatically up and down with zero administration.              |
| **Data Retention**  | Stores data for 24 hours by default (up to 365 days). Allows multiple apps to replay data. | **No data retention.** It is a pass-through service. Once delivered, the data is gone from the stream. |
| **Destinations**    | Custom consumers ([[EC2]] apps, AWS [[Lambda]], Kinesis Data Analytics).                   | Specific managed destinations (S3, Redshift, OpenSearch, Splunk, HTTP endpoints).                      |