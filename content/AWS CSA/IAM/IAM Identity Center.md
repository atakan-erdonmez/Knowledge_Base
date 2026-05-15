---
created: 2026-03-30T09:43
updated: 2026-03-30T09:43
---
Successor to AWS Single Sign-On

One login for all your:
- AWS accounts in AWS Organizations
- Business cloud apps (Salesforce, Box, M365..)
- SAML2.0-enabled apps
- EC2 Windows Instances


Identity providers:
- Built-in identity store in IAM Identity Center
- 3rd party: AD, OneLogin, Okta...


![[IAM Identity Center.png]]

## Fine-grained Permissions & Assignments
##### Multi-Account Permissions
Permissions sets are a collection of one or more IAM policies assigned to users and groups
##### Application Assignments
SSO access to many SAML 2.0 business apps. Provide required URLs, certificates and metadata
##### Attribute-Based Access Control (ABAC)
Fine-grained permissions based on users' attributes stored in Identity Center Identity Store. Like cost center, title, locale...
