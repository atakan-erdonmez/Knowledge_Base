---
tags:
  - aws
  - kubernetes
  - container
---

# EKS Anywhere
EKS Anywhere is a deployment option for Amazon Elastic Kubernetes Service (EKS) that allows you to create and manage Kubernetes clusters on your own infrastructure — such as on-premises servers or edge locations, outside of AWS. 

With EKS Anywhere running on [[AWS Outpost]], a company can modernize its Kubernetes stack with familiar AWS tooling without sending any data to the cloud.


# Other
You can encrypt cluster's etcd key-value store containing sensitive data. You can use KMS for this purpose. By default, these secrets are not encrypted. With KMS, you can encrypt them.