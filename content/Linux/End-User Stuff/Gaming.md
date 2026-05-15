---
created: 2026-03-30T09:43
updated: 2026-03-30T09:43
---
# Steam
Install steam, enable proton from settings

# Non-Steam
Use Heroic
`sudo apt install wine winetricks`
Install latest Proton-GE version


### 🧱 `DXVK` (DirectX → Vulkan)

- **What**: Translates DirectX 9/10/11 calls to Vulkan.
    
- **Why**: Greatly improves performance and compatibility for Windows games.
    
- **Use**: Always enable unless the game requires native DirectX via Wine.
    

---

### 🚀 `Esync` (Eventfd Synchronization)

- **What**: Replaces some Wine thread synchronization with faster Linux-native methods.
    
- **Why**: Reduces CPU overhead, improves multithreaded game performance.
    
- **Use**: Enable unless your system lacks `eventfd` support (almost all modern distros support it).
    

---

### ⚙️ `FSync` (Futex-based Synchronization)

- **What**: Even faster sync method than Esync, uses Linux `futex2` syscalls.
    
- **Why**: Improves performance in games with heavy multithreading (less overhead than Esync).
    
- **Use**: Requires kernel 5.16+ with `futex2` support and Proton-GE or recent Wine versions.
    

---

### 🔧 Summary of When to Use

| Feature | Performance Boost | Compatibility | Kernel Requirement           |
| ------- | ----------------- | ------------- | ---------------------------- |
| DXVK    | ✅ Huge            | ✅ High        | None                         |
| Esync   | ✅ Good            | ✅ High        | Modern kernels               |
| FSync   | ✅ Best            | ✅ High        | Kernel 5.16+ + glibc support |