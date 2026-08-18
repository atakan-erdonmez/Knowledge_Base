---
tags:
  - ssh
---
[[00_KnowledgeBase/3- Notes/Linux/Administration/SSH/index]]
This is run when the error 'WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!' shows up.

```
ssh-keygen -f "/home/atakan/.ssh/known_hosts" -R "192.168.10.55"
```