---
link:
  - "[[AWS]]"
tag:
  - "[[Compute]]"
  - "[[Containers|Containers]]"
---
You would still need to provision EC2 instances
# Auto Scaling
Amazon EKS supports two autoscaling products:

- Karpenter
- [[Kubernetes Cluster Autoscaler]]

The Kubernetes Cluster Autoscaler automatically adjusts the number of nodes in your cluster when pods fail or are rescheduled onto other nodes. The Cluster Autoscaler uses Auto Scaling groups.

Karpenter is a flexible, high-performance Kubernetes cluster autoscaler that launches appropriately sized compute resources, like Amazon EC2 instances, in response to changing application load. It integrates with AWS to provision compute resources that precisely match workload requirements.

# EKS Anywhere
EKS Anywhere is a deployment option for Amazon Elastic Kubernetes Service (EKS) that allows you to create and manage Kubernetes clusters on your own infrastructure — such as on-premises servers or edge locations, outside of AWS. 

With EKS Anywhere running on [[AWS Outpost]], a company can modernize its Kubernetes stack with familiar AWS tooling without sending any data to the cloud.


# Other
You can encrypt cluster's etcd key-value store containing sensitive data. You can use KMS for this purpose. By default, these secrets are not encrypted. With KMS, you can encrypt them.

---
# Index
```dataview
LIST
FROM ""
WHERE contains(link, [[EKS]])
```

