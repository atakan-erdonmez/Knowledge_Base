---
---
Amazon Machine Image
It is customization of an EC2 instance
- You can add your own software, config, OS, monitoring etc.
- Faster boot-configuration time because software is pre-packaged
- AMI are built for specific region, but can be copied

Copying an AMI to another region creates a new AMI and an associated snapshot (the EBS snapshot that AMI uses). Because AMIs are based on snapshots