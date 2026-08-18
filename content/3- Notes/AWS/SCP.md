---
link:
  - "[[IAM]]"
  - "[[AWS Organizations]]"
---
Service control policy (SCP) are one type of policy that can be used to **manage your organization**. Service control policy (SCP) offers central control over the maximum available permissions for all accounts in your organization, allowing you to ensure your accounts stay within your organization’s access control guidelines.

In service control policy (SCP), you can restrict which AWS services, resources, and individual API actions the users and roles in each member account can access. You can also define conditions for when to restrict access to AWS services, resources, and API actions. These restrictions even override the administrators of member accounts in the organization.

Please note the following effects on permissions vis-a-vis the service control policy (SCP):

- If a user or role has an IAM permission policy that grants access to an action that is either not allowed or explicitly denied by the applicable service control policy (SCP), the user or role can't perform that action.

- Service control policy (SCP) affects all users and roles in the member accounts, including root user of the member accounts.

- Service control policy (SCP) does not affect any service-linked role.