---
---
Based on PostgreSQL, but not for OLTP (online transaction processing)

---
Amazon Redshift is the most widely used cloud data warehouse. It makes it fast, simple, and cost-effective to analyze all your data using standard SQL and your existing Business Intelligence (BI) tools. It allows you to run complex analytic queries against terabytes to petabytes of structured and semi-structured data, using sophisticated query optimization, columnar storage on high-performance storage, and massively parallel query execution.

---

It's [[OLTP vs OLAP|OLAP]] - online analytical processing (analytics and data warehousing). 10x better performance, scales to PBs of data

- Columnar storage (instead of row-based) & parallel query engine
- Two modes: provisioned cluster and serverless cluster 
- Integrates with BI tools such as Quicksight or Tableu

## Snapshots
Has multi-AZ mode for some clusters
- You can restore a snapshot into a new cluster
- Automated (every 8 hours, every 5GB, or on a schedule) or manual retainment

## Redshift Spectrum
Query data that is already in [[S3]] without loading it. The query is then submitted to thousands of Redshift Spectrum notes

## Enhanced VPC Routing
research