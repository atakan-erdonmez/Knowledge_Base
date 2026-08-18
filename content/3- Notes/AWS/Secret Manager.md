---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
tag:
  - "[[00_KnowledgeBase/2- Tags/Security|Security]]"
---
Newer service, for storing sensitive secrets, with features like auto rotate and fine-grained access control. Not good for high volume application parameters. 

It has the option to enforce rotation
- Great integration with RDS


---
**IMPORTANT**
It is a little more expensive than [[AWS Systems Manager (SSM)#SSM Parameter Store|SSM Parameter Store]]. Secrets Manager is mainly for sensitive secrets that need features like **automatic rotation** and **fine-grained access control**. 

For storing application parameters that change infrequently and do not require rotation, AWS Systems Manager Parameter Store with `SecureString` is a more appropriate and cost-effective solution.