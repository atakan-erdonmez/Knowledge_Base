---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
  - "[[00_KnowledgeBase/3- Notes/Networking/Networking|Networking]]"
---
When you have an app with multiple edge locations, you can use Global Accelerator. It works by giving 2 anycast IP addresses to all edge locations. Supports **TCP & UDP**
 
> It is great when using blue-green deployment scenario

- So when you put the same IP, you will be directed to the closest edge location
- 2 IP is given for high availability


- It works with [[Elastic IP]], [[EC2]], [[Application Load Balancer]], [[Network Load Balancer]], public or private
- Consistent performance
	- Intelligent routing to lowest latency and fat regional failover
	- No issue with client cache (because IP doesn't change)
	- Internal AWS network
- Health Checks on your applications with automatic failover
- Increased security with integrated DDoS protection and only 2 external IP to be whitelisted



---
- [[Global Accelerator vs CloudFront]]
