---
created: 2026-03-30T09:43
updated: 2026-06-12T17:41
---
Easy way to set up and govern a secure and compliant multi-account AWS environment 
It uses [[AWS Organizations]] to create accounts

- Integrated security and compliance features like Service Control Policies (SCPs) and [[AWS Config]] rules. 
- By setting up a centralized VPC in a shared networking account, you can manage and distribute network resources across accounts using AWS Resource Access Manager (AWS RAM). 



Benefits:
- Automate the set up of your environment in a few clicks
- Automate ongoing policy management using guardrails
- Detect policy violations and remediate them
- Monitor compliance through an interactive dashboard

### Guardrails
Provides ongoing governance for you ControlTower environment
- Preventative Guardrail: Using SCPs (restrict region across all your accounts)
- Detective Guardrail: using [[AWS Config]] (identify untagged resources)