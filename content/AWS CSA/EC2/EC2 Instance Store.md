---
created: 2026-03-30T09:43
updated: 2026-06-15T09:25
tags:
  - ec2
  - aws
  - storage
---
High-performance hardware disk

- Better I/O performance
- Lose their storage if EC2 instance is stopped (**ephemeral**)
- Good for buffer / cache / scratch data / temporary content
- Risk of data loss if hardware fail


It is a low cost, good random I/O option for data that is temporary like cache, or copied across a fleet.