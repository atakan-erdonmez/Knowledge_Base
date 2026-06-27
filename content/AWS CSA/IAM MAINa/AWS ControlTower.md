---
link:
  - "[[AWS]]"
tag:
  - "[[2- Tags/Security|Security]]"
  - "[[Management]]"
---
Offers a straightforward way to set up and govern an AWS multi-account environment, following prescriptive best practices. AWS Control Tower orchestrates the capabilities of several other AWS services, including [[AWS Organizations]], AWS Service Catalog, and AWS [[IAM Identity Center]], to build a landing zone in less than an hour

It offers a **dashboard** to see provisioned accounts across your enterprise, guardrails enabled for policy enforcement, guardrails enabled for continuous detection of policy non-conformance, and non-compliant resources organized by accounts and OUs.


- Integrated security and compliance features like Service Control Policies (SCPs) and [[AWS Config]] rules. 
- By setting up a centralized VPC in a shared networking account, you can manage and distribute network resources across accounts using AWS [[Resource Access Manager (RAM)]]. 



Benefits:
- Automate the set up of your environment in a few clicks
- Automate ongoing policy management using guardrails
- Detect policy violations and remediate them
- Monitor compliance through an interactive dashboard


Features:
- It can detect OU changes, called **account or governance drift**
- It can integrate with [[EventBridge]] and [[SNS]] for notifications
### Guardrails
A guardrail is a high-level rule that provides ongoing governance for your overall AWS environment. It’s expressed in plain language. Through guardrails, AWS Control Tower implements _preventive_ or *detective* controls that help you govern your resources and monitor compliance across groups of AWS accounts.

- Preventative Guardrail: Using SCPs (restrict region across all your accounts)
- Detective Guardrail: using [[AWS Config]] (identify untagged resources)