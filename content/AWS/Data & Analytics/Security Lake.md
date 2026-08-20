---
---
Amazon Security Lake is a fully managed, purpose-built service designed to automatically collect, normalize, and centralize security-related data from various AWS accounts, Regions, services, and even third-party sources.

- It stores this data in Amazon [[S3]] buckets and formats it using the Open Cybersecurity Schema Framework (OCSF), which enhances compatibility with multiple analytics tools.
- Security Lake eliminates the need to build custom ETL pipelines or configure cross-service log ingestion manually, significantly reducing development effort. 
- It also integrates natively with AWS services like [[CloudTrail]], [[VPC Flow Logs|VPC Flow Logs]], [[Inspector, GuardDuty|GuardDuty]], and [[AWS Config]], providing a single authoritative view of security data across the organization. 
- With built-in support for log partitioning, retention, and access management, it delivers both centralization and scalability with minimal operational overhead. 
- The managed nature of Security Lake means there's minimal setup or custom coding, making it the lowest-effort and most scalable solution.