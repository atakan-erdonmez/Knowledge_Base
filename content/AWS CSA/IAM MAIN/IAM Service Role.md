---
link:
  - "[[iam"
---
A service role is an IAM role that a service assumes to perform actions on your behalf. Service roles provide access only within your account and cannot be used to grant access to services in other accounts. An IAM administrator can create, modify, and delete a service role from within IAM. When you create the service role, you define the `trusted entity` in the definition.


If you are going to use the role with Amazon [[00_KnowledgeBase/AWS CSA/EC2/EC2]] or another AWS service that uses Amazon EC2, you must store the role in an **instance profile**. An instance profile is a container for a role that can be attached to an Amazon EC2 instance when launched. An instance profile can contain only one role, and that limit cannot be increased. If you create the role using the AWS Management Console, the instance profile is created for you with the same name as the role.