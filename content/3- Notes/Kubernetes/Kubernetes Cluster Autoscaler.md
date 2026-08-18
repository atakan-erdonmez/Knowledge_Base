---
link:
  - "[[EKS]]"
tag:
  - "[[Container]]"
  - "[[Orchestration]]"
---
The [[Kubernetes]] Cluster Autoscaler is the recommended and most seamless solution to automatically manage the size of an [[EKS]] cluster's underlying compute resources. It works in tandem with the Kubernetes scheduler and continuously monitors the cluster for unschedulable pods—these are pods that cannot be scheduled due to a lack of available resources (CPU, memory, etc.) on the current set of [[EC2]] nodes.

When the Cluster Autoscaler detects unschedulable pods, it attempts to find an [[Auto Scaling Groups (ASG)]] attached to the EKS cluster that can satisfy the resource requirements of the pending pods. If it finds one, it automatically increases the desired capacity of that ASG, triggering the launch of new EC2 nodes. These new nodes register with the cluster and become available to host the previously unschedulable pods. In the same way, the Cluster Autoscaler also supports scale-in operations: it identifies underutilized nodes and safely drains and terminates them if their workloads can be moved elsewhere—leading to cost savings and higher resource efficiency.