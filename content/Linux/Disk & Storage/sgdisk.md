---
---

sudo sgdisk --backup=/tmp/sda.gpt /dev/sda


```
sudo sgdisk -e /dev/sdb
```

sgdisk -G


gdisk?? (gpt version of fdisk)


smartctl

sudo smartctl -a /dev/sdX -> check disk health??


- **`sgdisk --zap-all /dev/$d`** destroys the partition table itself: the GPT header at the start of the disk, the backup GPT header at the end, and the protective MBR. After this the disk has no partitions at all. It's the thorough version of "delete all partitions".

**`sgdisk -n1:0:0 -t1:8300 -c1:disk1 /dev/sda`** creates one partition with these parts:

- **`-n1:0:0`:** new partition number 1. The first `0` means start at the first usable, properly aligned sector. The second `0` means end at the last usable sector. Together they span the whole disk.
- **`-t1:8300`:** the type code for "Linux filesystem".
- **`-c1:disk1`:** sets a GPT partition name. It appears as `PARTLABEL` and as `/dev/disk/by-partlabel/disk1`. It's a human-readable label, and it makes it hard to mix up which disk is which.