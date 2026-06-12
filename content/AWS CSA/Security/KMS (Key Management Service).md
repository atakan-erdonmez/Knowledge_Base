---
created: 2026-03-30T09:43
updated: 2026-06-12T17:41
---
AWS handles encryption keys. It is the most common encryption in AWS. Integrated with IAM.

- Seamless integration with most AWS services
- Able to audit KMS key usage using CloudTrail
- Has both symmetric and asymmetric keys

### Type of KMS Keys
**AWS Owned Keys**: Free SSE-S3, SSE-SQS, SSE-DDB ...
**AWS Managed Key:** aws/servicename, like aws/rds
**Customer Managed Key**: $1/month + pay for API call


>When you use server-side encryption with AWS KMS (SSE-KMS), you can specify a customer-managed CMK that you have already created. SSE-KMS provides you with an audit trail that shows when your CMK was used and by whom. 