**Link**: [[00_KnowledgeBase/Linux/Linux|Linux]], [[Proxmox]]

**TRIM** (or **UNMAP**) is a storage command that lets an operating system tell the underlying disk drive (SSD or Thin Provisioned LVM/ZFS) which data blocks are no longer in use after files are deleted.


### Why It Matters

- **Without TRIM:** When you delete a file, the guest OS marks the space as empty in its own file table, but the physical host disk doesn't know. The host continues to hold onto those SSD blocks, assuming the data is still needed.
- **With TRIM:** The guest OS explicitly notifies the hypervisor and SSD controller: _"These specific block addresses are completely free."_

### fstrim command
With the command `fstrim -av`, host will trim. This command also runs automatically, using `fstrim.timer`.

#### fstrim.timer & fstrim.service
These timers run regularly to trim the storage.

- `systemctl list-timers fstrim.timer`