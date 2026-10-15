---
tags:
  - index
---
this is a test

ansible
[[Conditions]]

In order to pass an argument while running the playbook (like a host), you can use:
```
hosts: "{{ target | default('all_servers') }}"
```

and use `ansible-playbook deploy.yaml -e target=pve01`

%% Begin Waypoint %%
- **Modules**
	- [[copy]]
	- [[file]]
	- [[lineinfile]]
- [[Basics]]
- [[Conditions]]
- [[Environment Configuration]]
- [[Facts]]
- [[Getting Variable from .env without Copying]]
- [[group_vars]]
- [[00_KnowledgeBase/DevOps/Ansible/Inventory]]
- [[Playbooks]]
- [[Variables]]

%% End Waypoint %%
