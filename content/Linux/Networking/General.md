---
created: 2026-03-30T09:43
updated: 2026-05-12T10:46
---
#Networking #Linux

#### Activate Network Interface

![[ifconfig]]

# Tools (active and deprecated)
## 🟢 **Modern Tools (Actively Maintained)**

| Tool                     | Manages         | Status                 | Notes                                              |
| ------------------------ | --------------- | ---------------------- | -------------------------------------------------- |
| **NetworkManager**       | Everything      | ✅ Actively used        | Default in Ubuntu, Fedora, Mint, etc. GUI-friendly |
| **systemd-networkd**     | Interfaces only | ✅ Modern + Lightweight | No GUI. Ideal for servers                          |
| **iwd**                  | Wi-Fi (only)    | ✅ Modern               | Replaces `wpa_supplicant`                          |
| **[[systemd-resolved]]** | DNS             | ✅ Modern               | Handles `resolv.conf` & caching                    |
| **netplan**              | YAML frontend   | ✅ Ubuntu-specific      | Configures NM or `systemd-networkd`                |
| **ConnMan**              | All             | ⚠️ Aging               | Lightweight, mostly used on embedded systems       |
| **wicked**               | All             | ✅ OpenSUSE’s default   | Full-featured backend                              |

---

## ⚠️ **Legacy / Deprecated Tools**

|Tool/Script|OS|Status|Example Config Location|
|---|---|---|---|
|**ifupdown**|Debian|❌ Deprecated|`/etc/network/interfaces`|
|**network**|RHEL/CentOS|❌ Deprecated (as of RHEL 9)|`/etc/sysconfig/network-scripts/ifcfg-*`|
|**wpa_supplicant**|All|✅ Still works but fading|Used with NM or standalone|
|**resolv.conf (manual)**|All|Still used, but mostly symlinked now|`/etc/resolv.conf`|