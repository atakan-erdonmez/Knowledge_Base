---
link:
  - "[[EC2|EC2]]"
---
If AWS detects that an instance is unavailable due to an underlying hardware or software issue, there are two mechanisms that can automatically restore instance availability—[simplified automatic recovery](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-configuration-recovery.html) and [Amazon CloudWatch action based recovery](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/cloudwatch-recovery.html). Restoring instance availability is also known as _instance recovery_.

During the instance recovery process, AWS will attempt to move your instance from the host with the underlying hardware or software issue **to a different host**. If successful, the instance recovery process will appear to the instance as an unplanned reboot. You can [verify if instance recovery occurred](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/verify-if-automatic-recovery-occurred.html).

> Terminated instances cannot be recovered

## What is changed in recovery
- **What stays the same:** Because AWS is just moving your configuration to a new host, your **Instance ID**, **Private IP**, and **Elastic IP** stay exactly the same. Your applications or network rules pointing to those identifiers won't break.

- **What is lost:** Because the original physical server is unresponsive or failing, AWS cannot copy what was actively running in the physical RAM. Therefore, **in-memory (RAM) data** and **Instance Store data** (temporary physical storage attached to the host) are lost. Standard public IPv4 addresses are also released during the reboot/host change cycle.
---
Further reading: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-recover.html