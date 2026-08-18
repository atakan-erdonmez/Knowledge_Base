---
link:
  - "[[AWS]]"
tag:
  - "[[Databases|Databases]]"
---
> For further reading about keys: [[DynamoDB Partition & Sort Key]]

It is a fully managed, highly available NoSQL database. Distributed, scales to massive workloads, replication with multiple AZ.

Provides **<mark style="background: #ADCCFFA6;">single-digit millisecond latency</mark>** for reads and writes at any scale

- Fast and consistent performance (single digit ms)
- Low cost and auto scaling
- No maintenance or patching, always available
- Standard and Infrequent Access (IA) data

It is made of *tables*. Each table has a primary key, and can have an infinite number of rows. Each item has attributes, which can be increased over time. Max item size=400kb

> Can replace [[ElastiCache]] for caching


**Features:** [[DynamoDB Features]]
## Read/Write Capacity Modes
### Provisioned Mode (default)
Specify read-writes beforehand. Pay for provisioned RCU (Read Capacity Units) and WCU (Write Capacity Units). Possibility to add auto-scaling for RCU&WCU.

> You can use auto-scaling to adjust provisioned capacity

### On-Demand Mode
Automatic scaling. Much more expensive. Great for *unpredictable workloads* and *sudden spikes*. Good option if:
- You create new tables with unknown workloads.
- You have unpredictable application traffic.
- You prefer the ease of paying for only what you use.

---
# Index
```dataview
LIST
FROM ""
WHERE contains(link, [[DynamoDB]])
```
