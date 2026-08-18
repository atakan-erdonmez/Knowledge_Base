---
link:
  - "[[AWS]]"
tag:
  - "[[00_KnowledgeBase/2- Tags/Security|Security]]"
---
**AWS Security Hub** is a cloud security management service that aggregates, organizes, and prioritizes security alerts (called "findings") from across your AWS environment into a single dashboard.

Here are the key takeaways for your notes:

- **Centralized Dashboard:** It acts as a single pane of glass, collecting security alerts from native AWS services (like [[Inspector, GuardDuty]], [[Amazon Macie]], and IAM Access Analyzer) as well as third-party partner security tools.

- **Compliance Checking:** It automatically runs continuous automated configuration checks against industry security standards and best practices (such as CIS Benchmarks, PCI-DSS, and the AWS Foundational Security Best Practices).

- **Security Score:** It provides an overall security score across your accounts so you can instantly gauge your security posture.

- **Automated Remediation:** It integrates with [[EventBridge]], allowing you to automatically trigger [[Lambda]] functions to fix security issues the moment they are detected.