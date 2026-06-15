---
---
Data lake is a central place to have all your data for analytics purposes

- Fully managed service that makes it easy to setup a data lake in days (instead of months)
- Discover, cleanse, transform, and ingest data with automation (collecting, moving, cataloging...)
- Combine structured and unstructured data
- Out-of-the-box blueprints: S3, RDS, Relational & NoSQL DB
- Fine-grained access control
- Built on top of AWS Glue (though user do not interact with it directly)

One of the advantages is centralized access control. It centralize all services, and makes managing permissions easier

---
**AWS Lake Formation** is a service that makes it easy to set up a secure data lake in days. A data lake is a centralized, curated, and secured repository that stores all your data, both in its original form and prepared for analysis. A data lake enables you to break down data silos and combine different types of analytics to gain insights and guide better business decisions.

Amazon S3 forms the storage layer for Lake Formation. If you already use S3, you typically begin by registering existing S3 buckets that contain your data. Lake Formation creates new buckets for the data lake and imports data into them. AWS always stores this data in your account, and only you have direct access to it.

AWS Lake Formation is integrated with AWS Glue which you can use to create a data catalog that describes available datasets and their appropriate business applications. Lake Formation lets you define policies and control data access with simple “grant and revoke permissions to data” sets at granular levels. You can assign permissions to IAM users, roles, groups, and Active Directory users using federation. You specify permissions on catalog objects (like tables and columns) rather than on buckets and objects.

You can get data from multiple accounts.