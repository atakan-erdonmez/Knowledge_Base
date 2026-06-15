---
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


>[!INFO]
> If you don't have enough bandwidth, you can use [[Snow Family|AWS Snowcone]], DataSync agent is preinstalled




> [!question] About the usage
> As far as I understand, it is best for continuous backups and sync process. [[S3]] Transfer Acceleration & Multi-part Upload is faster, so that should be preferred for one-time uploads.
