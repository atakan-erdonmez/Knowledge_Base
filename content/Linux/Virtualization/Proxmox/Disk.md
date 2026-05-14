---
created: 2026-03-30T09:43
updated: 2026-03-30T09:43
---
To pass-through a disk to a VM:
In proxmox shell:

lsblk
ls -l /dev/sidk/by-id

copy the ata....

qm set <VM_ID> -scsi1 /dev/disk/by-id/<your-disk>
