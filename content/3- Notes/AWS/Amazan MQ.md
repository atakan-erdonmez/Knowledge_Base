---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
tag:
  - "[[Message&Queue]]"
---
It is a managed message broker service for RabbitMQ and ActiveMQ.

It is to use traditional on-premises solutions to be used on AWS like MQTT, AMQP, Openwire, WSS...

---
Amazon MQ is a managed message broker service that makes it easy to migrate to a message broker in the cloud. A message broker allows software applications and components to communicate using various programming languages, operating systems, and formal messaging protocols. Amazon MQ supports Apache ActiveMQ, RabbitMQ, and other message broker engine types.

A cluster deployment is a logical grouping of three RabbitMQ broker nodes behind a Network Load Balancer, each sharing users, queues, and a distributed state across multiple Availability Zones (AZ). In a cluster deployment, Amazon MQ automatically manages broker policies to enable classic mirroring across all nodes, ensuring high availability (HA). Each mirrored queue consists of one main node and one or more mirrors. Each queue has its own main node. All operations for a given queue are first applied on the queue’s main node and then propagated to mirrors. Amazon MQ creates a default system policy that sets the `ha-mode` to all and `ha-sync-mode` to automatic. This ensures that data is replicated to all nodes in the cluster across different Availability Zones for better durability.