---
link:
  - "[[Aurora]]"
---
## Aurora Database Cloning
It is used to create a new cluster that initially shares the same data, but a separate and independent volume.

- Create a new Aurora DB cluster from an existing one
- Faster than snapshot & restore, because it uses copy-on-write protocol where only writes happen when there are changes
