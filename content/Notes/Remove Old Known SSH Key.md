---
created: 2026-05-17T18:06
updated: 2026-06-03T21:12
tags:
  - ssh
---
[[SSH]]
This is run when the error 'WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!' shows up.

```
ssh-keygen -f "/home/atakan/.ssh/known_hosts" -R "192.168.10.55"
```