---
created: 2026-03-30T09:43
updated: 2026-05-12T11:17
---
sudo sgdisk --zap-all /dev/sdb
sudo sgdisk --backup=/tmp/sda.gpt /dev/sda
```
sudo partprobe /dev/sdb
```

```
sudo sgdisk -e /dev/sdb
```

sgdisk -G


gdisk?? (gpt version of fdisk)


smartctl

sudo smartctl -a /dev/sdX -> check disk health??