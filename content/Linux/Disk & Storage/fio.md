---
tags:
  - disk
  - storage
---

fio is a program used to identify read&write speed of storage devices like thumb drives, SSDs and HDDs.


### Write Speed
```
fio --name=write_test --directory=/path/to/usb --size=1G --rw=write --bs=1M --direct=1 --numjobs=1 --time_based --runtime=30 --end_fsync=1
```

### Read Speed
```
fio --name=read_test --directory=/path/to/usb --size=1G --rw=read --bs=1M --direct=1 --numjobs=1 --time_based --runtime=30
```


### Mechanical HDDs (Internal & External)

HDDs rely on spinning platters, so sequential throughput differs significantly from random IOPS.

- **Sequential Read/Write (Large files):**

    ```
    fio --name=hdd_seq --directory=./ --size=2G --rw=write --bs=1M --direct=1 --end_fsync=1
    ```
  
- **Random 4K Read/Write (Small files/OS responsiveness):**

    ```
    fio --name=hdd_rand --directory=./ --size=512M --rw=randrw --rwmixread=70 --bs=4k --direct=1 --runtime=60 --time_based
    ```


### SATA & NVMe SSDs (Internal & External)

SSDs excel at parallel I/O. Adding queue depth (`--iodepth`) and multiple threads (`--numjobs`) exposes their maximum performance.

- **Sequential Max Bandwidth:**

    ```
    fio --name=ssd_seq --directory=./ --size=4G --rw=rw --rwmixread=70 --bs=1M --direct=1 --ioengine=libaio --iodepth=16
    ```
  
- **4K Random IOPS (High Queue Depth):**

    ```
    fio --name=ssd_iops --directory=./ --size=2G --rw=randrw --rwmixread=70 --bs=4k --direct=1 --ioengine=libaio --iodepth=32 --numjobs=4 --group_reporting
    ```