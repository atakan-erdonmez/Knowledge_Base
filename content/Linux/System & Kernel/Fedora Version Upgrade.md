---
created: 2026-05-11T15:26
updated: 2026-05-11T15:26
---
To upgrade a major version (43 to 44 in this example) you can use these commands.
```
sudo dnf upgrade --refresh
sudo dnf install dnf-plugin-system-upgrade
sudo dnf system-upgrade download --releasever=44
sudo dnf5 offline reboot
```

- `sudo dnf upgrade --refresh`: Upgrade system with --refresh for ignoring local cache, downloading latest metadata
- `sudo dnf install dnf-plugin-system-upgrade`: Plugin necessary for OS update
- `sudo dnf system-upgrade download --releasever=44`: Download the required packages for system upate
- `sudo dnf5 offline reboot`: Installs the update.

**BACKING UP HOME DIRECTORY IS HIGHLY SUGGESTED**