---
created: 2026-03-30T09:43
updated: 2026-05-06T13:29
---
It is a declarative way of outlining your AWS infrastructure for all resources.

For example, you can:
- Define a security group
- Create multiple EC2 instances
- Create S3 Buckets
and so on.


**Benefits**: 
- IaC
- Cost advantage, estimate costs easier
- Productivity, you dont have to do ordering
- Templates, don't do everything from scratch


## Services Role
CloudFormation needs IAM roles to actually provision resources. However, if you want to give users access to CloudFormation, but not resources itself, you should use *Service Role*