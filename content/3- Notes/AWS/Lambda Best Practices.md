---
link:
  - "[[Lambda]]"
---
- Since AWS Lambda functions can scale extremely quickly, it's a good idea to deploy a Amazon CloudWatch Alarm that notifies your team when function metrics such as `ConcurrentExecutions` or `Invocations exceeds the expected threshold`


- If you intend to reuse code in more than one AWS Lambda function, you should consider creating an [[Lambda Layer]] for the reusable code


- Since Lambda allocates compute power in proportion to the memory, you can over-allocate memory. However, you shouldn't over-allocate function time out. That might cause extra charges