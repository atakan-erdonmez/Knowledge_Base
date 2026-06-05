---
created: 2026-03-30T09:43
updated: 2026-06-05T10:14
---
Managed NFS that can be mounted on many EC2. It supports multi-AZ. **IT IS VPC-bound, regional!**
- Highly available, scalable, expensive (3x gp2), pay per use
- Use cases: content management, web serving, data sharing
- Users NFSv4.1 protocol
- Uses security group to control access to EFS
- Compatible with Linux based AMI
- Scales automatically, pay-per-use, no capacity planning

> For exam: EFS is POSIX-compliant.
## Performance & Storage Classes
#### EFS Scale
- 1000s of concurrent NFS clients, 10 GB+ /s throughput
- Grow to Petabyte-scale, automatically

#### Throughput Mode
- **Bursting** - 1 TB = 50MiB/s + burst of up to 1000MiB/s (throughput relies on the amount of data stored)
- **Provisioned** - set your throughput regardless of storage size (gives consistent throughput regardless of the amount of data stored)
- **Elastic** - automatically scales throughput up or down based on your downloads

#### Performance Mode Setting
- General Purpose (default): latency-sensitive use cases (web server, CMS etc)
- Max I/O - higher latency, throughput, highly parallel (big data, media processing)


NOTE: To mount the EFS to EC2 using the EFS helper, you need to install amazon-efs-utils
```
sudo yum -y install amazon-efs-utils
```