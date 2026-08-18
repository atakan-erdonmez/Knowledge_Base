---
link:
  - "[[AWS]]"
tag:
  - "[[00_KnowledgeBase/2- Tags/Security|Security]]"
---

Layer 7 protection against common web vulnerabilities

Deploy on:
- [[Application Load Balancer]]
- [[API Gateway]]
- [[CloudFront]]
- [[AppSync]] GraphQL API
- [[Cognito]] User Pool

> **NOT** on EC2

You can define Web ACL Rules:
- IP Set: up to 10k IP 
- HTTP hearders, body, URI strings
- Size constraints, geo-match
- Rate-based rules - DDoS protection

Can be used to prevent DDoS attacks 

You can have complex filtering, like block a country except some IP addresses.