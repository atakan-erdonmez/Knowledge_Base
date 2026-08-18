---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
tag:
  - "[[00_KnowledgeBase/2- Tags/Security|Security]]"
---
AWS handles encryption keys. It is the most common encryption in AWS. Integrated with [[IAM]].

- Seamless integration with most AWS services
- Able to audit KMS key usage using [[CloudTrail]]
- Has both symmetric and asymmetric keys

### Type of KMS Keys
**AWS Owned Keys**: Free SSE-S3, SSE-SQS, SSE-DDB ...
**AWS Managed Key:** aws/servicename, like aws/rds
**Customer Managed Key**: $1/month + pay for API call


>When you use server-side encryption with AWS KMS (SSE-KMS), you can specify a customer-managed CMK that you have already created. SSE-KMS provides you with an audit trail that shows when your CMK was used and by whom. 


# CloudHSM
AWS CloudHSM (Hardware Security Module) is a cloud-based hardware security service that allows you to generate and use your own cryptographic keys on dedicated, single-tenant hardware appliances inside the AWS cloud. 

Its primary purpose is to help you meet strict corporate, contractual, and regulatory compliance requirements for data security (such as FIPS 140-2 Level 3) by giving you exclusive administrative control over the tamper-resistant hardware, ensuring that not even AWS employees can access your keys.