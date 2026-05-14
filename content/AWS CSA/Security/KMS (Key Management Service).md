---
created: 2026-03-30T09:43
updated: 2026-03-30T09:43
---
AWS handles encryption keys. It is the most common encryption in AWS. Integrated with IAM.

- Seamless integration with most AWS services
- Able to audit KMS key usage using CloudTrail
- Has both symmetric and asymmetric keys

### Type of KMS Keys
**AWS Owned Keys**: Free SSE-S3, SSE-SQS, SSE-DDB ...
**AWS Managed Key:** aws/servicename, like aws/rds
**Customer Managed Key**: $1/month + pay for API call
