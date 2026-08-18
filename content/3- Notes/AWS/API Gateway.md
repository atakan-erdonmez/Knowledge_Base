---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
tag:
  - "[[00_KnowledgeBase/2- Tags/Networking|Networking]]"
  - "[[Development]]"
---
It is a way for clients to talk to AWS resources. They access the REST API, which then proxies to AWS resources. You pay for what you use.

> Amazon API Gateway supports stateless RESTful APIs as well as stateful WebSocket APIs.


>[!TIP]
>API Gateway supports throttling (rate limiting) and caching for increased performance.


[[Lambda]] + API Gateway: No infrastructure
- Support for the WebSocket protocol
- Handle different environments, API versions, and security
- Transform and validate requests and responses

> Can implement **caching** for quick & easy performance increase
## Integration
#### Lambda Function
- Invoke functions
- Easy way to expose REST API backed by AWS [[Lambda]]
#### HTTP
- Expose HTTP endpoints in the backend
- Example: internal HTTP API on premise, [[Application Load Balancer|ALB]]...
- Why? Add rate limiting, caching, user auth, API keys...
#### AWS Service
- Expose any AWS API through the API Gateway
- Example: start an AWS [[Step Functions]] workflow, post a message to [[SQS]]

## Endpoint Types
#### Edge Optimized
- Default, for global clients
- Requests are routed through [[CloudFront]] Edge locations (improved latency)
- API Gateway still lives in only one region
#### Regional:
- For clients with the same region
- Can manually combine with [[CloudFront]] (more control)
#### Private:
- Can only be accessed from [[VPC]] using interface VPC endpoint (ENI)
- Use a resource policy to define access

## Resource Policy
API Gateway supports resource policies, which are [[IAM]]-style JSON policies that you attach directly to your REST or HTTP APIs. These policies can use IpAddress and NotIpAddress conditions to enforce fine-grained network controls. 

By configuring a policy that explicitly denies all IPs except for the trusted internal IP ranges, the company can ensure that only requests originating from its internal network are allowed to invoke the API.


## OIDC-Compliance & JWT
Amazon API Gateway HTTP APIs support native JWT authorizers, allowing developers to configure the API to automatically validate JWT tokens issued by an OIDC-compliant identity provider, such as Auth0, Okta, or Amazon Cognito. This eliminates the need for custom authentication logic in Lambda functions and reduces both latency and cost. HTTP APIs are optimized for low-latency, high-performance workloads and are more cost-effective than REST APIs, making them ideal for modern, serverless applications that require standard JWT validation and claim-based access control.


## Caching
You can implement caching in API Gateway to cache your endpoint's responses.


--- 
# Index
```dataview
LIST
FROM ""
WHERE contains(link, [[API Gateway]])
```
