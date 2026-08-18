---
link:
  - "[[Elastic Load Balancer (ELB)|Elastic Load Balancer (ELB)]]"
  - "[[Auto Scaling Groups (ASG)]]"
---
By default, ASG uses EC2 health check, which only checks if the **instance is up** and responsive. It doesn't check the application status. If the OS is intact, it is a pass.


ELB on the other hand can check health based on other factors like port, path, TCP connection attempts etc. It **never terminates instances**, but can mark as unhealthy and stop sending traffic.


You can configure ASG to use ELB's health checks in addition to EC2 status checks.
When you turn this on, the ASG delegates the definition of "healthy" to the load balancer:

1. The **ELB** sends an application-level ping (e.g., checking if `/health` returns a `200 OK`).
2. If the application crashes, the **ELB** marks the instance as unhealthy and stops routing traffic to it.
3. The **ASG** sees that the ELB has marked the instance as unhealthy.
4. The **ASG** steps in, terminates the dead instance, and provisions a fresh one.