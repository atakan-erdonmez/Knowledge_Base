---
link:
  - "[[AWS]]"
  - "[[!NEW_MOCs/Storage|Storage]]"
---
Launch 3rd party high-performance file systems on AWS. Fully managed service
- FSx for Lustre
- FSx for Windows File Server
- FSx for NetApp ONTAP
- FSx for OpenZFS
## FSx for Windows File Server
Fully managed Windows file system shared drive.
- Supports SMB & Windows NTFS
- Active Directory integration, ACLs, user quotas
- **Can be mounted on Linux EC2 instances**
- You can use Microsoft Distributed File System (DFS) Namespaces to group multiple file systems together, like connecting on-premise and cloud
- Supports DFS

Amazon FSx works with Microsoft Active Directory to integrate with your existing Microsoft Windows environments. You have two options to provide user authentication and access control for your file system: AWS Managed Microsoft Active Directory and Self-managed Microsoft Active Directory.

Take note that after you create an Active Directory configuration for a file system, you can’t change that configuration. However, you can create a new file system from a backup and change the Active Directory integration configuration for that file system. These configurations allow the users in your domain to use their existing identity to access the Amazon FSx file system and to control access to individual files and folders.


## FSx for Lustre
Lustre is a type of parallel distributed file system, for large-scale computing. The name is derived from "Linux" and "cluster".

- Used for machine learning, **High Performance Computing (HPC)**, video processing, financial modeling, electronic design automation
- Scales up to 100s GB/s, millions of IOPS, sub-ms latencies
- Seamless integration with S3, read and write with S3
- Can be used from on-premises servers (VPN or Direct Connect)


## FSx for NetApp ONTAP
Managed NetApp ONTAP on AWS. (ONTAP is a proprietary OS from NetApp for network systems)
- File system compatible with NFS, SMB, iSCSI
- Move workloads running on ONTAP or NAS, works with Linux, Windows, macos, vmware cloud...
- Storage shrinks and grows automatically
- Snapshots, replication, lost-cost, compression and data de-duplication
- Point-in-time instantaneous cloning (helpful for testing new workloads)

The Amazon FSx for NetApp ONTAP features Multi-AZ file systems designed to ensure continuous availability across AWS Availability Zones, providing high availability for your Windows Server workloads. It offers consistent sub-millisecond file operation latencies with SSD storage, essential for block storage workloads in Windows environments. FSx for NetApp ONTAP fully supports block storage protocols like iSCSI, commonly used in Windows Server settings, and it works seamlessly with the SMB protocol, ensuring compatibility with Windows Server and related applications.

#### NetApp SnapMirror
The NetApp SnapMirror replication solution is built into NetApp ONTAP for Business Continuity and Disaster Recovery (BCDR) purposes, and it is built on ONTAP snapshots technology. You can use SnapMirror to replicate data from a source FSx for ONTAP file system to the destination FSx for ONTAP file system.

## Amazon FSx for OpenZFS
- File system compatible with NFS (v3, v4, v4.1, v4.2)
- Move workloads running on ZFS, works with linux, macos, windows, amazon workspaces, appstream...
- Up to 1.000.000 IOPS with < 0.5ms latency
- Snapshots, compression and low cost; Point-in-time instantaneous cloning


### OpenZFS vs ONTAP
|**Feature**|**FSx for NetApp ONTAP**|**FSx for OpenZFS**|
|---|---|---|
|**Primary Protocols**|NFS, SMB, iSCSI (Multi-protocol)|NFS (v3 through v4.2)|
|**OS Support**|Linux, Windows, macOS|Primarily Linux / Unix Unix-like|
|**Key Strength**|Enterprise data management & versatility|Ultra-low latency & high IOPS throughput|
|**Built-in Tiering**|Yes (Automated SSD to Capacity Pool)|No (Requires manual volume management)|

## FSx File System Deployment Options
2 file system:

### Scratch File System
- Temporary storage, data not replicated
- High burst (6x faster, 200MBps per TiB)
- Usage: short-term processing, optimize costs

### Persistent File System
- Long-term storage, data replicated within same AZ
- Replace failed within minutes
- Usage: long-term processing, sensitive data