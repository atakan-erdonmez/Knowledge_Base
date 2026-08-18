---
link:
  - "[[AWS]]"
tag:
  - "[[Development]]"
  - "[[CI-CD]]"
---
AWS CodeConnections, formerly AWS CodeStar Connections, is designed to securely connect AWS services, such as CodePipeline, with third-party source control systems like GitHub, Bitbucket, and GitLab. It allows the automatic triggering of pipelines based on events such as code push and pull requests. All communications between AWS and the source control system are encrypted using Transport Layer Security (TLS 1.0 or later). All CodeConnections API calls are logged automatically via AWS [[CloudTrail]], ensuring the integration is auditable.