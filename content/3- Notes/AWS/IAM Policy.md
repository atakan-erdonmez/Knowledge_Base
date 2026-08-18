---
link:
  - "[[IAM]]"
---
**IAM Policies** are essential for controlling access to AWS resources. IAM policies enable you to set fine-grained permissions for AWS account users, groups, or roles. By creating IAM policies, you can control who can access your resources and what actions they can perform. These policies are written in a JSON format and consist of one or more statements. Each statement represents an access control rule that defines the conditions under which specific actions are permitted or denied.

An IAM policy statement includes several key elements:

- **Effect:** This element determines whether the statement allows or denies access. The effect can be set to “Allow” or “Deny” to permit or prohibit actions explicitly.

- **Action:** The action specifies the specific AWS service actions allowed or denied. Actions are represented by unique names, such as ec2:RunInstances for launching EC2 instances or s3:GetObject for retrieving objects from S3 buckets.

- **Resource:** The resource element identifies the AWS resources the actions apply. It uses Amazon Resource Names (ARNs) to specify the specific resources or resource types, such as arn:aws:s3:::my-bucket/* for all objects in an S3 bucket.

- **Condition** (optional): Conditions provide additional constraints on when the policy’s effect applies. For example, you can define conditions based on time, IP address, or request parameters to further control access.