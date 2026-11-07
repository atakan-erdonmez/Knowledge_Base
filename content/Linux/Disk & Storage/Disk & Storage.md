---
tags:
  - index
title: Disk & Storage
---
# Linux disk management tools

Disk work happens in layers. You identify the disk and check its health, clear old signatures, write a partition table (MBR or GPT), and tell the kernel to re-read it. Then you create a filesystem and mount it. Partitioning tools only change the table and never touch the data inside partitions. Some write only after you confirm (fdisk, gdisk), and others write immediately (sgdisk, parted). `sdX` names can change between reboots, so identify disks by serial or `/dev/disk/by-id/` before anything destructive.

Typical order: `lsblk` → `smartctl` → `badblocks` → `wipefs` → partition → `partprobe` → `mkfs` → `blkid` → fstab → mount

## Identify and inspect

- **lsblk**: lists disks and partitions as a tree, with sizes, models, serials and mountpoints.

- **blkid**: prints the UUID, label and filesystem type of a device. The UUID is what goes in `/etc/fstab`.

## Health and testing

- **smartctl** (smartmontools): reads a disk's SMART health data and runs self-tests. "PASSED" alone doesn't prove the disk is healthy, so read the attributes. **smartd** is the background service that sends alerts.

- **badblocks**: scans the whole surface for unreadable blocks. Its `-w` mode is destructive, which makes it good for burn-in on a disk you're about to wipe. It takes many hours on large drives.

## Clearing old data

- **wipefs**: erases filesystem, RAID and partition-table signatures without overwriting the data. Run it on old partitions before deleting the table, or stale signatures can reappear.

## Partitioning

- **fdisk**: interactive util-linux partitioner for MBR and GPT. Nothing is written until `w`.

- **cfdisk**: a menu-driven screen version of fdisk.

- **sfdisk**: scriptable util-linux partitioner. It can dump a table to a file and restore it.

- **gdisk / cgdisk / [[sgdisk]]**: GPT-only tools: interactive, menu-driven and scriptable. sgdisk writes immediately and can back up, restore, repair and clone tables.

- **[[parted]]**: handles many label types and accepts friendly units like `100%`. It writes immediately and can resize partitions, but it can't back up a table.

- **[[partprobe]]**: makes the kernel re-read the partition table without a reboot.

## Filesystems

- **mkfs.ext4**: creates an ext4 filesystem on a partition. `-m 0` removes the 5% reserved space, which is wasted on data disks.

- **tune2fs**: changes ext4 settings after creation, such as the label and reserved space.

- **e2fsck**: checks and repairs an unmounted ext4 filesystem.
- 
%% Begin Waypoint %%
- [[Disk Directory]]
- [[du command]]
- [[fio]]
- [[fstab file]]
- [[fstrim]]
- [[hdparm LINK]]
- [[LVM]]
- [[MBR & GPT]]
- [[mount]]
- [[Parted]]
- [[partprobe]]
- [[RAID]]
- [[resize2fs]]
- [[sgdisk]]

%% End Waypoint %%
