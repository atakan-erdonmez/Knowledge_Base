---
created: 2026-03-30T09:43
updated: 2026-05-06T16:24
---
It is the generic info about the client. It is run by the module 'setup'. It is run automatically.

```
tasks:
- debug:
	  var: ansible_facts
```

You can disable gathering facts in play via:
`gather_facts: no`