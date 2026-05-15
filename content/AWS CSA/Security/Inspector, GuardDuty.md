---
created: 2026-03-30T09:43
updated: 2026-03-30T09:43
---
Inspector looks **inside** your resources to find "structural" weaknesses like software bugs or open doors you forgot to lock.

**What it does:** Scans your EC2 instances, Lambda functions, and Container images (ECR) for known software vulnerabilities (CVEs) and unintended network exposure.


# GuardDuty
GuardDuty stands on the perimeter and watches **behavior**. It doesn't care if your software is old; it cares if someone is actually trying to break in or if your server is acting "weird."

- **What it does:** Uses Machine Learning to analyze logs (VPC Flow Logs, DNS logs, CloudTrail) to spot malicious activity like crypto-mining, credential theft, or communication with known "bad" IP addresses.