---
link:
  - "[[Elastic Load Balancer (ELB)|Elastic Load Balancer (ELB)]]"
---
**Link:** [[Elastic Load Balancer (ELB)]]

It is layer 7. Load balancing to multiple HTTP applications across machines (target group).
- It can load balance to multiple apps on same machine (containers)
- Supports HTTP/2, WebSocket, gRPC and support redirects
- They are great fit for microservices & container-based applications (docker & Amazon ECS)
- **Cannot** get an [[Elastic IP]]
### Target Groups
- [[EC2]] instances (can be managed by an Auto Scaling Group) - HTTP
- [[ECS (Elastic Container Service)]] tasks (managed by ECS itself)  - HTTP
- [[Lambda]] functions - HTTP request is translated into a JSON event
- IP Addresses - must be private IPs

> It has advanced routing policies, it can be based on content


>[!Warning]
>You cannot assign a [[Elastic IP]] to the ALB. It can only be assigned to [[Network Load Balancer]].

### Conditions to Filter
ALB can filter based on:
- Host Header
- Path Pattern
- Source IP
- HTTP Header
- HTTP Request Method
- Query String


> It **CANNOT** block based on geographic or IP based conditions