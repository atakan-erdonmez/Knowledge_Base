---
created: 2026-03-30T09:43
updated: 2026-03-30T09:43
---


.bash_profile: Login shells. Calls for .bashrc

.bashrc: Interactive non-login shells

**~~Note: Local variables won’t work with environmental variables~~**

```jsx
A=30
B=40
C=`expr $A + $B`
echo $C ## output=70
```

3 types of variables:

Local: A=20

Environmental: export A=20

System: Created by kernel




set: Show all variables OR show local variables (?)
unset: delete a variable

env: Show environmental variables

local: Show local variables
