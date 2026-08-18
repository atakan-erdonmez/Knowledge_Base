---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
tag:
  - "[[00_KnowledgeBase/2- Tags/Databases|Databases]]"
---
- Aurora is a proprietary technology from AWS (not open sourced)
- Postgres and MySQL are both supported as Aurora DB (that means your drivers will work as if Aurora was a Postgres or MySQL database)
- Aurora is “AWS cloud optimized” and claims 5x performance improvement over MySQL on RDS, over 3x the performance of Postgres on [[RDS]]
- Aurora storage automatically grows in increments of 10GB, up to 128 TB.
- Aurora can have up to 15 replicas and the replication process is faster than MySQL (sub 10 ms replica lag)
- Failover in Aurora is instantaneous. It’s HA (High Availability) native. 
- Aurora costs more than RDS (20% more) – but is more efficient

## High Availability and Read Scaling
- 6 copies of your data across 3 AZ:
	- 4 copies out of 6 needed for writes
	- 3 copies out of 6 need for reads
	- Self healing with peer-to-peer replication
	- Storage is striped across 100s of volumes

- One Aurora Instance takes writes (master)
- Automated failover for master in less than 30 seconds
- Master + up to 15 Aurora Read Replicas serve reads
- Support for Cross Region Replication

---
If you have an Amazon Aurora Replica in the same or a different Availability Zone, when failing over, Amazon Aurora flips the canonical name record (CNAME) for your DB Instance to point at the healthy replica, which in turn is promoted to become the new primary. Start-to-finish failover typically completes within 30 seconds.

If you are running Aurora Serverless and the DB instance or AZ becomes unavailable, Aurora will automatically recreate the DB instance in a different AZ.

If you do not have an Amazon Aurora Replica (i.e., single instance) and are not running Aurora Serverless, Aurora will attempt to create a new DB Instance in the same Availability Zone as the original instance. This replacement of the original instance is done on a best-effort basis and may not succeed, for example, if there is an issue that is broadly affecting the Availability Zone.

---

## Endpoints
There are writer and reader endpoint.

### Writer endpoint (cluster endpoint)
- It will point to the master, which is the only DB that can write to storage
- Even when master fails over, client will connect to writer endpoint and will be redirected to the new master, providing failover 

> **ONLY THE MASTER CAN WRITE**

### Reader endpoint
- Read Replicas can auto scale, and it can be hard for apps to track which replica is where
- Reader endpoint act as a connection load balancer, connecting all read replicas
### Instance Endpoint

- **What it is:** A direct connection string to a **single, specific database instance** within an Aurora cluster.

- **Use Case:** Used primarily by DBAs for direct troubleshooting, performance diagnostics, or connecting to one specific node.

- **Caveat:** It bypasses Aurora’s automatic high availability and failover logic, so it shouldn't be used in your application's core production code.
### Custom Endpoint

- **What it is:** A custom DNS endpoint that load-balances traffic across a **filtered subset of instances** that you choose.

- **Use Case:** Used for **workload isolation (preventing "noisy neighbors")**. You can route lightweight production application reads to a group of smaller instances, while directing heavy, unoptimized analytical/BI reporting workloads to a separate, larger instance.

- **Configuration:** Can be defined statically (explicitly adding specific nodes) or dynamically (excluding specific nodes).

## Features
- Automatic fail-over
- Backup and Recovery
- Isolation and security
- Industry compliance
- Push-button scaling
- Automated Patching with Zero Downtime
- Advanced Monitoring
- Routine Maintenance
- Backtrack: restore data at any point of time without using backups

# Advanced Features
## Auto Scaling
You can set up auto scaling, so read replicas will be scaled accordingly. Reader endpoint will extend to cover newly generated replicas.
## Custom Endpoints
You create a custom endpoint to cover some replicas. Like if you have 2 stronger instances, you can redirect them to your custom endpoint for running analytical queries
## Serverless 
Automated database instantiation. Good for infrequent, intermittent or unpredictable workload
> Great for improving **write** capacity

- No capacity planning needed
- Pay per second, can be more cost-effective
> One ACU (Aurora Capacity Point) is 2 GiB of memory.






## Additional
### Babelfish
Babelfish allows Aurora PostgreSQL to understand T-SQL (Microsoft SQL Server's query language) and SQL Server wire protocol, enabling applications to communicate with Aurora using SQL Server-style queries with minimal code changes. This is ideal for minimizing application code refactoring.


### Parallel Query
Research


---
# Index
```dataview
LIST
FROM ""
WHERE contains(link,[[Aurora]])
```
