---
created: 2026-03-30T09:43
updated: 2026-03-30T09:43
---
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amdgpu.ppfeaturemask=0xffffffff"
## 🧩 1. What is `GRUB_CMDLINE_LINUX_DEFAULT`?

- It's a **GRUB config variable** found in `/etc/default/grub`.
    
- It defines **default kernel command-line parameters** passed **on normal boots** (not recovery mode).
    
- These parameters affect the **Linux kernel's behavior during and after boot.**
    

---

## 🧩 2. `quiet splash` – What are these?

|Parameter|Meaning|
|---|---|
|`quiet`|Suppresses most boot messages from the kernel. You won’t see things like "Started XYZ", "Mounted ABC", etc.|
|`splash`|Tells the init system (and display manager) to show a **splash screen** (like a logo or animation).|

Used together, `quiet splash` gives a **clean boot screen** (e.g., Ubuntu logo instead of kernel logs).

> 🧠 You can remove these if you want to **see verbose boot messages**, e.g. for troubleshooting.

## 🧩 3. `amdgpu.ppfeaturemask=0xffffffff` – What is this?

- This is a **kernel parameter** for AMD GPU driver (`amdgpu`).
    
- `ppfeaturemask` controls **PowerPlay features** — like overclocking, fan curve control, power states, etc.
    
- By default, many of these are **locked down by the driver**.
    

By setting:

`amdgpu.ppfeaturemask=0xffffffff`

You enable **all PowerPlay features**, even **undocumented or unsupported** ones.

### 🛠️ Why use this?

- To control **GPU fan curve**, **power limits**, or **clock speeds** from userspace using tools like:
    
    - `rocm-smi`
        
    - `pp_od_clk_voltage`
        
    - Custom fan/OC scripts
        

> ⚠️ Be careful: Enabling unsupported features can **cause instability or damage** if you're careless.

## 🧪 How to Apply Changes

1. Edit the file:
    `sudo nano /etc/default/grub`

2. Modify the `GRUB_CMDLINE_LINUX_DEFAULT` line.
    
3. Save and run:
    `sudo update-grub`

4. Reboot.

## 🧠 How to Learn About Them

### 🔹 1. **Official Linux Kernel Docs**

- **Canonical source** for many options.
    
- 🔗 https://www.kernel.org/doc/html/latest/admin-guide/kernel-parameters.html
    
- Contains nearly all **upstream-supported** options.
    
- Searchable by keyword (e.g., `amdgpu`, `quiet`, `nomodeset`, etc.)
    

---

### 🔹 2. `modinfo` for Module-Specific Parameters

For **driver/module-specific options** (like `amdgpu.ppfeaturemask`):

bash

CopyEdit

`modinfo amdgpu`

Gives info about parameters, description, and default values (if documented).

---

### 🔹 3. Read Current Boot Parameters

bash

CopyEdit

`cat /proc/cmdline`

Shows what parameters were passed at boot time.