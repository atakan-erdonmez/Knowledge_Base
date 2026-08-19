---
link:
  - "[[AWS]]"
tag:
  - "[[00_KnowledgeBase/OLD-2- Tags/Security|Security]]"
---
Identity and Access management, Global service (no need to create a new IAM role in a new region)

You can use groups. One user can be in multiple groups. Groups can't include other groups

---
# Identities & Resources

#### Identities (The "Who")

- **Root User:** The account creator identity. It has complete, un-restrictable access to all resources.

- **IAM Users:** Permanent individual identities created inside AWS to represent a specific person or application. They use static credentials (passwords or Access Keys).

- **IAM Groups:** A logical collection of IAM Users. You cannot attach a policy directly to multiple users easily; instead, attach the policy to a Group, and the users inherit those permissions.

- **IAM Roles:** Dynamic, temporary identities. A role does not have permanent credentials. Instead, another entity (a user, an EC2 instance, an AWS service) **assumes** the role to obtain short-lived security tokens via the AWS Security Token Service (STS).
#### Resources (The "What")

- **Any object or asset** within an AWS service (an S3 bucket, an EC2 instance, a DynamoDB table, or an IAM user itself).

- Resources are universally identified by an **ARN (Amazon Resource Name)**, matching this exact structural syntax: `arn:partition:service:region:account-id:resource-id`

---
# Policy Types
### Identity-Based Policies

These are **attached directly to an IAM User, Group, or Role**. They dictate exactly **what that identity is allowed to do** across AWS.

- **Managed Policies:** Standalone, reusable policies. Can be _AWS-Managed_ (created and updated by AWS, like `AdministratorAccess`) or _Customer-Managed_ (built and managed by you).

- **Inline Policies:** Policies embedded strictly into a single identity. If you delete the identity, the policy is destroyed with it.

### Resource-Based Policies

These are attached directly to the **Resource** itself (e.g., an S3 bucket policy, an SQS queue policy, or an encryption key in KMS).

- Unlike identity policies, resource-based policies **must contain a `Principal` block** explicitly declaring _who_ is allowed to access that specific resource.

- They are highly useful for **Cross-Account Access** because they allow a resource in Account B to directly permit an identity in Account A to access it without making that user assume a role.

### Trust Policies vs. Permission Policies (The Role Boundary)

When configuring an **IAM Role**, you encounter two completely distinct JSON policies that work together:
#### Trust Policy (Who can assume this role?)

Every role has an attached Trust Policy (officially called the **AssumeRole Policy Document**). It defines which external principals are allowed to log into or "wear" this role.

- _Example:_ If an EC2 instance needs to read from S3, the role's Trust Policy must state that the `ec2.amazonaws.com` service is a trusted principal.
#### Permission Policy (What can this role do once assumed?)

Once a trusted entity successfully assumes the role, this policy dictates what operations the session is allowed to perform across AWS.

- _Example:_ Allowing `s3:GetObject` on a specific bucket.\


**Further Reading:**
- [[IAM Service Role]]
- [[IAM Execution Role]]

---


## IAM Policies Structure

**Consists of**
- Version: policy language version
- Id: ID for the policy (optional)
- Statement: one or more individual statements (required)
**Statements consists of**
- Sid: Statement ID (optional)
- Effect: Allow or deny
- Principal: account/user/role to which this policy applies to
- Action: list of actions this policy allows or denies
- Resource: list of resources which the actions applies to
- Condition: (optional)


## Access Keys, CLI, SDK
Management console: Web interface
SDK: AWS Software development kit

You use access keys to access CLI and SDK


# CLI Config
use `aws configure` and put your region and access keys. Now you can access AWS resources with CLI.
**THIS SHOULD NEVER BE DONE** due to security

Access keys are a way to access your AWS. However, since the access keys are stored as plain-text, it is not a good practice security-wise

# IAM Role
These are just like users, but for services instead of actual people.

You put an IAM role to the EC2 instance for example, and permissions work on that IAM role


# Index
```dataview
LIST
FROM ""
WHERE contains(link, [[IAM]])
```
---