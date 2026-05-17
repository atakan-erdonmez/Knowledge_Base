---
created: 2026-03-30T09:43
updated: 2026-05-17T17:58
---
https://wiki.debian.org/fstab

## 🔹 What happens _without_ `noatime`:

Every time you **read** a file (e.g., `cat`, `ls`, open in app), Linux **updates the file's “access time” (atime)** — even if nothing changes in the file.

That means:

- It writes metadata to disk **just for reading**
    
- On HDDs, this causes unnecessary disk I/O and head movement
    

---

## 🔹 What `noatime` does:

It tells the system:

> “Don’t update the file’s access time when it’s read.”





nofail: Continue boot if drive fails


- `noauto`: prevents mounting at boot.
    
- `x-systemd.automount`: mounts **only when accessed**, without manual `mount`.
    
- `noatime`: already good, prevents unnecessary writes.
    
- `nofail`: allows boot to continue even if RAID is missing or inactive.

# default includes
### 🔍 `defaults` includes:


`rw, suid, dev, exec, auto, nouser, async`

#### Meaning:

| Option   | Meaning                           |
| -------- | --------------------------------- |
| `rw`     | Read/write                        |
| `suid`   | Allow set-user-identifier bits    |
| `dev`    | Interpret character/block devices |
| `exec`   | Allow execution of binaries       |
| `auto`   | Mount automatically at boot       |
| `nouser` | Only root can mount               |
| `async`  | Async I/O                         |


`x-systemd.automount` is a **systemd-specific mount option** used in `/etc/fstab` to enable **on-demand mounting**.

---

### 🔧 What it does:

It creates a **systemd automount unit** for the mount point, so the filesystem is **not mounted at boot**, but is **mounted automatically** the moment something tries to access it.