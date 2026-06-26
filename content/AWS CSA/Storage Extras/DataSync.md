---
link:
  - "[[2- Tags/Storage]]"
---
Move large amount of data to and from. 
- On-premises / other cloud to AWS (NFS, SMB, HDFS, S3 API...) - needs agent
- AWS to AWS (different storage services) - no agent needed

Can synchronize to:
- [[S3|Amazon S3]] (any storage classes, including Glacier)
- [[EFS - Elastic File System|EFS]]
- [[FSx]]

- Replication tasks can be scheduled hourly, daily, weekly
- File permissions and metadata are preserved

---

**AWS DataSync** makes it **simple and fast** to move **large amounts of data** online between on-premises storage and [[S3]],  [[EFS - Elastic File System]], or [[FSx#FSx for Windows File Server]]. Manual tasks related to data transfers can slow down migrations and burden IT operations. DataSync eliminates or automatically handles many of these tasks, including scripting copy jobs, scheduling, and monitoring transfers, validating data, and optimizing network utilization. The DataSync software agent connects to your Network File System (NFS), Server Message Block (SMB) storage, and your self-managed object storage, so you don’t have to modify your applications.

DataSync can transfer hundreds of terabytes and millions of files at speeds up to 10 times faster than open-source tools, over the Internet or AWS Direct Connect links. You can use DataSync to migrate active data sets or archives to AWS, transfer data to the cloud for timely analysis and processing, or replicate data to AWS for business continuity. Getting started with DataSync is easy: deploy the DataSync agent, connect it to your file system, select your AWS storage resources, and start moving data between them. You pay only for the data you move.
- You can directly upload to Glacier without lifecycle policy

>[!INFO]
> If you don't have enough bandwidth, you can use [[Snow Family|AWS Snowcone]], DataSync agent is preinstalled





