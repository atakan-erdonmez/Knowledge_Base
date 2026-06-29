---
link:
  - "[[AWS]]"
tag:
  - "[[Storage]]"
---
Elastic Block Store is a network drive that you attach to [[EC2]]. It persists.
They are bound to specific AZ
Low cost, low performance
Good for long-term storage

## Features
- When you create an EBS volume in an Availability Zone, it is automatically replicated within that zone to prevent data loss due to a failure of any single hardware component.
- After you create a volume, you can attach it to any EC2 instance in the same Availability Zone
- Amazon EBS Multi-Attach enables you to attach a single Provisioned IOPS SSD (io1) volume to multiple Nitro-based instances that are in the same Availability Zone. However, other EBS types are not supported.
- An EBS volume is off-instance storage that can persist independently from the life of an instance. You can specify not to terminate the EBS volume when you terminate the EC2 instance during instance creation.

- EBS volumes support live configuration changes while in production which means that you can modify the volume type, volume size, and IOPS capacity without service interruptions.
- Amazon EBS encryption uses 256-bit Advanced Encryption Standard algorithms (AES-256)

- EBS Volumes offer 99.999% SLA.

>Maximum backup retention period for automated backup is only 35 days. For longer, you can use [[AWS Backup]]
## Volume Types
There are 6 types of volumes
1. **gp2/gp3 (SSD):** General purpose SSD, price-performance, can handle **bursts** via accumulated burst credits
2. **io1/io2 Block Express (SSD):** Highest-performance SSD volume for mission-critical low-latency or high-throughput workloads (**provisioned IOPS**). Great for database workloads. They support multi-attach
3. **st1 (HDD):** Low cost HDD volume designed for frequently access, throughput-intensive workloads like big data, data warehouses, log processing etc
4. **sc1 (HDD):** Lowest cost HDD volume designed for less frequently accessed workloads 

> **Only gp2/gp3 and io1/io2 Block Express can be used as boot volumes**

### Multi-Attach
- Only available in io1/io2 Block Express
- Up to 16 EC2 instances at a time
- Must use a file system that's cluster-aware (not XFS, EXT4 etc)

### EBS Encryption
- Has minimal impact on latency
- Leverages keys from KMS (AES-256)
##### How to Encrypt
To encrypt an EBS volume, you need to create a snapshot, copy it and encrypt it, then create a volume from it. 
Or you can take an unencrypted snapshot, create volume from it and while doing that, enable encryption


##### Encryption Coverage
When you create an encrypted EBS volume and attach it to a supported instance type, the following types of data are encrypted:
- Data at rest inside the volume
- All data moving between the volume and the instance
- All snapshots created from the volume
- All volumes created from those snapshots

##### Encryption by Default
You can configure your AWS account to enforce the encryption of the new EBS volumes and snapshot copies that you create. For example, Amazon EBS encrypts the EBS volumes created when you launch an instance and the snapshots that you copy from an unencrypted snapshot.

Encryption by default has no effect on existing EBS volumes or snapshots. The following are important considerations in EBS encryption:

- Encryption by default is a Region-specific setting. If you enable it for a Region, you cannot disable it for individual volumes or snapshots in that Region.
- When you enable encryption by default, you can launch an instance only if the instance type supports EBS encryption.
- Amazon EBS does not support asymmetric KMS keys.
### Snapshots
Backup of EBS, stored in [[S3]] but not directly accessible through S3.
Not necessary to detach the volume, but *recommended*
- You can copy snapshots across AZ or region
#### Snapshot Features
- EBS Snapshot Archive: Move snapshot to "archive" tier which is %75 cheaper
- Takes within 24-72 hours for restoring the archive
- You can use the EBS volume while taking the snapshot
#### Recycle Bin for EBS Snapshots
Retention period to recover accidental deletion
- Setup rules to retention (1 day to 1 year)
#### Fast Snapshot Restore (FSR)
- It is a fast snapshot that takes no latency on initialization, expensive

### Data Lifecycle Manager (DLM)
**Amazon Data Lifecycle Manager (DLM)** automates the creation, retention, and deletion of Amazon Elastic Block Store (EBS) snapshots. It simplifies EBS volume management by allowing you to define policies that govern the lifecycle of these snapshots, ensuring regular backups are created and obsolete snapshots are automatically removed.

Here are the following features that Amazon Data Lifecycle Manager is capable of:

 - Protect valuable data by enforcing a regular backup schedule.
- Create standardized AMIs that can be refreshed at regular intervals.
- Retain backups as required by auditors or internal compliance.
- Reduce storage costs by deleting outdated backups.
- Create disaster recovery backup policies that backup data to isolated Regions or accounts.