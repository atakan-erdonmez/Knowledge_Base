---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
tag:
  - "[[FinOps]]"
---
AWS Cost Explorer is a highly visual analytics tool that allows you to view, analyze, and forecast your historical cost and usage data. It features an interactive dashboard where you can filter and group data by dimensions such as AWS service, region, linked account, or custom cost allocation tags, making it easy to identify long-term spending trends and isolate specific cost drivers.


# Cost Explorer API
You can programmatically query your cost and usage data via the **Cost Explorer API**. You can query for aggregated data such as total monthly costs or total daily usage. You can also query for granular data, such as the number of daily write operations for DynamoDB database tables in your production environment.

By using the AWS Cost Explorer API, the company can programmatically access the usage cost-related data they need on specific services. The pagination feature allows for the efficient retrieval of large datasets.