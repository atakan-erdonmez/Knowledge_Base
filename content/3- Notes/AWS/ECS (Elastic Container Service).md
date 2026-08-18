---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
tag:
  - "[[Containers|Containers]]"
  - "[[Compute]]"
---
## EC2 Launch Type
Launch ECS Tasks on ECS Clusters

In this launch type, you must provision and maintain the infra. Your ECS/ECS Cluster will have special [[EC2]] instances that each has ECS agent.
- Priced on EC2 instances and EBS volumes used

## Fargate Launch Type
Fargate is serverless container solution. In this type, you don't provision the infrastructure, it is serverless. You just create tasks definitions, AWS runs ECS tasks based on resources. Priced on vCPU and memory

> **Task Definition**: It is similar to [[Docker Compose]] file. You specify ports, image, launch type etc.
## ECS Integrations
#### EC2 Instance Profile 
> EC2 launch type only

- Used by ECS agent, makes API calls to ECS service
- Send logs to CloudWatch, pull Docker image from ECR

#### ECS Task Role
- Allows each task to have a specific role
- Use different roles for the different ECS services you run
- Task role is defined in the task definition

#### ECS Task Execution Role
An IAM role used by the **Amazon ECS container agent** to perform infrastructure-level tasks _before_ your container actually starts.

[[IAM Execution Role]]


| **Feature**         | **EC2 Instance Profile (Host Level)**                                             | **ECS Task Execution Role (Agent Level)**                                       | **ECS Task Role (Application Level)**                                          |
| ------------------- | --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| **Who uses it?**    | The **EC2 operating system** / host VM.                                           | The **ECS Container Agent** running on the host.                                | The **actual application code** inside the container.                          |
| **What is it for?** | Joining the cluster, sending host metrics, running the host agent.                | Pulling private Docker images from ECR, injecting secrets from Secrets Manager. | Giving your app permission to query DynamoDB, read from S3, write to SQS, etc. |
| **Launch Type?**    | **EC2 only** (Fargate manages the infrastructure, so no instance profiles exist). | Both EC2 and Fargate.                                                           | Both EC2 and Fargate.                                                          |
## Load Balancer Integration
- [[Application Load Balancer]] is supported for most use cases
- [[Network Load Balancer]] recommended for only high throughput/performance

## Data Volumes (EFS)
You can mount [[EFS - Elastic File System]] onto ECS tasks. Works with EC2 and Fargate
- Use cases: Persistent multi-az shared storage
- [[S3]] cannot be mounted as filesystem

## Monitoring
**The following metrics are available for instances:**
- CPU Utilization
- Disk Reads
- Disk Read Operations
- Disk Writes
- Disk Write Operations
- Network In
- Network Out
- Status Check Failed (Any)
- Status Check Failed (Instance)
- Status Check Failed (System)
- 
**The following metrics are available for ECS Service:**
- **ECSServiceAverageCPUUtilization**—Average CPU utilization of the service.
- **ECSServiceAverageMemoryUtilization**—Average memory utilization of the service.
- **ALBRequestCountPerTarget**—Number of requests completed per target in an Application Load Balancer target group.