---
link:
  - "[[IAM]]"
---
It is an **IAM role assigned directly to an AWS compute resource** ([[Lambda]], [[EC2]]). It provides the necessary credentials for that resource to **perform actions and access other AWS services** automatically when running your application code.


### Key Characteristics

- **Identity-Based Application:** Unlike resource-based policies attached to a target asset, an execution role is attached directly to the computing service executing your logic.

- **Temporary Security Tokens:** It eliminates the security risk of hardcoding static IAM Access Keys or secrets into deployment packages. The compute resource requests short-lived credentials dynamically via AWS [[Security Token Service (STS)]].

- **The "Badge" Analogy:** It acts as an automated security badge given to a resource, allowing it to interact with downstream systems like [[DynamoDB]], [[S3]], or [[CloudWatch Logs]] on your behalf.


### Core Configuration Components

An execution role requires two distinct IAM policy documents to function:

1. **Trust Policy (AssumeRole):** Defines the specific AWS service principal (e.g., `lambda.amazonaws.com` or `ecs-tasks.amazonaws.com`) permitted to assume the role.

2. **Permissions Policy:** Defines the granular API access rights (e.g., `s3:GetObject`, `dynamodb:PutItem`) granted to the resource once the code executes.