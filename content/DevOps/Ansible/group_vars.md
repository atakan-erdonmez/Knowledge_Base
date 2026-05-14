---
created: 2026-04-06T09:24
updated: 2026-05-06T16:27
---
- **vars_files variable**: Although not necessarily required (Ansible automatically uses the files under `group_vars/all/` in every playbook), still included for readability. It uses the passwords inside the file for Ansible vault. It uses the password inside to encrypt Restic backups

##### Why group_vars is the best practice
1. **Automatic Loading:** If your inventory is in the `ansible/` folder, Ansible will automatically look for a `group_vars/` folder in that same directory. Any variables inside `group_vars/all/` are applied to **every** host in your lab automatically. You won't need to manually include the file in your Kavita playbook anymore.
2. **Scalability:** As your homelab grows (e.g., adding Home Assistant, Jellyfin, or a _Second_ Docker VM), you can just add new secrets to that one `secrets.yaml` file, and they will be available globally.
3. **Cleanliness:** It keeps your "Logic" (the `services/` playbooks) separated from your "Data" (the `ansible/` inventory and variables).
