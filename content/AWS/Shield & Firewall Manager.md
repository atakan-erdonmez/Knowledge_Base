---
link:
  - "[[AWS]]"
tag:
  - "[[00_KnowledgeBase/OLD-2- Tags/Security|Security]]"
  - "[[00_KnowledgeBase/OLD-2- Tags/Networking|Networking]]"
---
# Shield
DDoS prevention service

### Shiel Standard
Free service that is automatically activated
- Provides protection from attacks such as SYN/UDP floods, reflection attacks and other L3-4 attacks

### Shield Advanced
Optional DDoS mitigation service ($3000 per month per organization)
- Protect against more sophisticated attack on EC2, ELB, CloudFront, AWS Global Accelerator and Route 53
- 24/7 access to AWS DDoS response team
- Protect against higher fees during usage spikes due to DDoS

# Firewall Manager
Manage rules in all accounts of an [[AWS Organizations]]. Create common set of security rules on:
- [[AWS WAF]]
- [[Shield & Firewall Manager|Shield Advanced]]
- [[VPC]] Security groups (mandate common master sgs, audit existing ones, enforce standard rules etc)
- [[Security Groups & NACLs|NACL]]
- [[Network Firewall]]
- [[Route 53]] Resolver DNS Firewall
- AWS Marketplace Third-Party firewalls

#### Key Responsibilities

1. **Automatic Compliance & Remediation:** It continuously monitors for non-compliant resources (e.g., if a developer creates a new ALB without WAF attached or alters a master security group) and can automatically remediate the resource to bring it back into compliance.

2. **Hierarchical Enforcement:** It lets corporate security administrators enforce global baseline guardrails while still giving individual application teams the flexibility to write their own specific granular rules underneath.f


# Network Firewall
![[Network Firewall]]