---
tags:
  - aws
  - ec2
  - scripting
  - ip
---
In order to get metadata about your running [[EC2]] instance, you can run curl or get to receive metadata info, like private IP, public IP, AMI-ID, MAC, metrics etc.

```
curl http://169.254.169.254/latest/meta-data/
```