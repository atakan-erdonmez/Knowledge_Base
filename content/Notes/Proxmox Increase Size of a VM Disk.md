---
tags:
  - "#proxmox"
  - vm
created: 2026-05-11T15:26
updated: 2026-05-14T14:10
---

[[00_KnowledgeBase/Linux/Virtualization/Proxmox/index]], [[LVM]], [[00_KnowledgeBase/Linux/Virtualization/Proxmox/Disk|Proxmox_Disk]], [[VM Creation]

## Step 1: Increase Size in GUI
Go to Hardware -> Disk -> Resize on the top

## Step 2: Increase Size of FS
```
sudo growpart /dev/sda 1
sudo resize2fs /dev/sda1
```


## If LVM is Used
```
sudo pvresize /dev/sda3
sudo lvextend -l +100%FREE /dev/mapper/<vg-name>-<lv-name>
sudo resize2fs /dev/mapper/<vg-name>-<lv-name>   # ext4
```