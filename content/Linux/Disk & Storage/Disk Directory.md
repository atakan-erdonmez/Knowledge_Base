

`/dev/disk/` is a set of symlink folders that udev builds automatically. Each one gives you another way to refer to the same device, other than the unstable `sdX` name:

|Folder|Identifies a device by|
|---|---|
|`by-id`|hardware model and serial number|
|`by-uuid`|filesystem UUID|
|`by-label`|filesystem label (the `-L` we set with `mkfs`)|
|`by-partlabel`|GPT partition name (the `-c` we set with `sgdisk`)|
|`by-partuuid`|GPT partition GUID|
|`by-path`|physical slot (controller and port)|

A link only appears if the device has that property.

`/dev/disk/by-id/` is the one that lists nearly everything, so use it if you want to see all your disks.