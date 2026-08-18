---
link:
  - "[[00_KnowledgeBase/3- Notes/Linux/Virtualization/Proxmox/index]]"
---
1. Shutdown all containers and VMs
2. Edit `/etc/hostname` and `/etc/hosts` and rename
3. Reboot
4. Move VM and CT configs to the new directory in `/etc/pve/nodes`
```
## VMs
mv /etc/pve/nodes/OLD_NAME/qemu-server/*.conf /etc/pve/nodes/NEW_NAME/qemu-server/ 2>/dev/null

## CTs
mv /etc/pve/nodes/OLD_NAME/lxc/*.conf /etc/pve/nodes/NEW_NAME/lxc/ 2>/dev/null
```

5. Copy historical performance data to the new node (optional)
```
cp -r /var/lib/rrdcached/db/pve2-node/OLD_NAME /var/lib/rrdcached/db/pve2-node/NEW_NAME 2>/dev/null
```

6. Remove old directory
```
rm -rf /etc/pve/nodes/OLD_NAME
rm -rf /var/lib/rddcached/db/pve2-node/OLD_NAME
```