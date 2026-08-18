---
link:
  - "[[AWS]]"
tag:
  - "[[00_KnowledgeBase/2- Tags/Logging|Logging]]"
  - "[[00_KnowledgeBase/2- Tags/Monitoring|Monitoring]]"
  - "[[Data&Analytics]]"
---
Open-source successor to [[OpenSearch & ELK (Elasticsearch)|ElastiSearch]].


In [[DynamoDB]], queries only exist by primary key or indexes.

With OpenSearch, you can search any field, even partially matches. It is common to use it as a complement to another database.

- Two modes: managed or serverless
- Does *not* natively support SQL (can be enabled via plugin)
- Ingestion from Kinesis Data Firehose, AWS IoT, and CloudWatch logs
- Comes with OpenSearch Dashboards

> Further read: [[OpenSearch & ELK (Elasticsearch)]]