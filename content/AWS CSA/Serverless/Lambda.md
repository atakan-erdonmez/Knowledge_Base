---
link:
  - "[[AWS]]"
tag:
  - "[[Compute]]"
  - "[[2- Tags/Serverless|Serverless]]"
---

| EC2                        | Lambda                                   |
| -------------------------- | ---------------------------------------- |
| Virtual servers            | Virtual functions - no servers to manage |
| Limited by RAM and CPU     | Limited by time - short executions       |
| Continuously running       | Run on-demand                            |
| Scaling means intervention | Scaling is automated                     |
It is great for **event-driven functions**
## Advantages
- Easy pricing with pay per request and compute time
- Integrated with whole AWS suite, supports many programming languages
- Easy monitoring with CloudWatch 
- Easy to get more resources per functions (up to 10GB of RAM, increasing ram will increase CPU and network performance)

## IAM Integration
In [[IAM]], you can have both resource-based policies and  execution roles. 

- <mark style="background: #FFB86CA6;">Resource based policies dictate *who* can invoke the function</mark>
- <mark style="background: #FFB86CA6;">Execution roles dictate *what* can the function do</mark>
## Limits
#### Execution
- Memory allocation: 128MB - 10GB (1MB increments)
- Maximum execution time: 900 second (15 minutes)
- Environment variables (4KB)
- Disk capacity - temp space: 512MB to 10GB
- Concurrency executions: 1000 (can be increased)
#### Deployment
- Function deployment size (compressed zip): 50MB
- Size of uncompressed deployment (code + dependencies): 250MB
- /tmp dir can be used

## SnapStart
Normally, a function goes throuth "init -> invoke -> shutdown" and init can take a long time. By pre-initializing the function, you can increase performance.

When you publish a new version, it gets inited and snapshoted for low latency access.

## Network
By default, Lambda functions are out of your VPC (Amazon managed VPC), so it can't access your resources. If you want it in your VPC, you need to define VPC ID, the Subnets and Security Groups.

One of the most common use cases is with [[RDS#RDS Proxy|RDS Proxy]]



## Others
### ENV Encryption
When you create or update Lambda functions that use environment variables, AWS Lambda encrypts them using the AWS Key Management Service. When your Lambda function is invoked, those values are decrypted and made available to the Lambda code.

The first time you create or update Lambda functions that use environment variables in a region, a default service key is created for you automatically within AWS KMS. This key is used to encrypt environment variables. However, if you wish to use encryption helpers and use KMS to encrypt environment variables after your Lambda function is created, you must create your own AWS KMS key and choose it instead of the default key. The default key will give errors when chosen. Creating your own key gives you more flexibility, including the ability to create, rotate, disable, and define access controls, and to audit the encryption keys used to protect your data.


### Lambda with Container Image Support
AWS Lambda with Container Image Support is a fully managed, serverless compute service that allows you to run your applications without provisioning or managing servers. 

Traditionally, AWS Lambda functions were deployed using code written in supported programming languages, but with container image support, you can now package and deploy your application as a Docker container. This provides more flexibility, as it allows you to use custom runtimes or include dependencies that are difficult to manage in a traditional Lambda function deployment. Lambda functions with container images can be up to 10 GB in size, enabling you to deploy large, complex applications with ease.

### Function URL
**Lambda function URLs** are HTTP(S) endpoints dedicated to your Lambda function. You can easily create and set up a function URL using the Lambda console or API. Once created, Lambda generates a unique URL endpoint for your use.


---
# Index
```dataview
LIST
FROM ""
WHERE contains(link,[[Lambda]])
```
