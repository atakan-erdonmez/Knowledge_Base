---
created: 2026-03-30T09:43
updated: 2026-03-30T09:43
---
[How it works?](https://tailscale.com/blog/how-tailscale-works#mesh-networks)

# 🔧 What is Tailscale?

- A **zero-config VPN** built on **WireGuard**
    
- Connects all your devices into a **private network** (called a _tailnet_)
    
- Handles **NAT traversal**, **peer discovery**, and **key exchange** automatically
    
- Uses **DERP servers** as fallback relays if direct connection fails


# ⚙️ How Tailscale Works

1. You install the **Tailscale client** on each device
    
2. You log in with your Tailscale account (Google, Microsoft, etc.)
    
3. Devices get a **static private IP** (100.x.x.x) and can resolve each other by name (`device-name.tailnet-name.ts.net`)
    
4. Devices try **peer-to-peer connection** using NAT hole punching (STUN)
    
5. If direct P2P fails, Tailscale uses **DERP** (relay server fallback)


## 🧱 Comparison with Raw WireGuard

| Feature         | **Tailscale**     | **Raw WireGuard**       |
| --------------- | ----------------- | ----------------------- |
| Encryption      | ✅ Yes (WireGuard) | ✅ Yes (WireGuard)       |
| NAT traversal   | ✅ Built-in        | ❌ Manual (port forward) |
| Peer discovery  | ✅ Automatic       | ❌ Manual                |
| Key management  | ✅ Automatic       | ❌ Manual                |
| DNS / Hostnames | ✅ MagicDNS        | ❌ Manual or none        |
| Relay fallback  | ✅ DERP            | ❌ You must build it     |
|                 |                   |                         |


# STUN - TURN - DERP
## 🛰️ STUN (Session Traversal Utilities for NAT)

### 📌 Purpose:

Helps a device behind a NAT/router **discover its own public IP and port**.

### 🛠️ How It Works:

1. Client contacts a public **STUN server**
2. STUN server replies: “You appear as IP `x.x.x.x`, port `yyyy`”
3. Now the client knows what IP/port others must send to

### 🎯 Use Case:

- Enables **NAT hole punching**
- Used in WebRTC, Tailscale, VoIP, etc.

### 🧠 Limitation:

- Works best with **cone NAT**
- Fails with **symmetric NAT** or **CGNAT**

---

## 🚪 TURN (Traversal Using Relays around NAT)

### 📌 Purpose:

Relays traffic when **STUN fails** (i.e., no direct P2P possible).

### 🛠️ How It Works:

1. Both clients connect to a **TURN server**
2. TURN server relays traffic between them
3. Acts as a neutral **middleman**

### 🎯 Use Case:

- Last-resort method for **guaranteed connectivity**
- Higher latency, more bandwidth usage
- Used in WebRTC, Tailscale (equivalent: DERP)

---

## 📦 DERP (Tailscale's TURN Alternative)

### 📌 Purpose:

Tailscale’s custom **relay network** for encrypted traffic when P2P fails.

### 🛠️ How It Works:

- Like TURN, but:
    
    - **No STUN setup needed**
        
    - Always encrypted end-to-end (via WireGuard)
        
    - Geographically distributed
        
- Only sends one side’s traffic through relay; the other side may have direct
    

### 🎯 Use Case:

- **Reliable fallback** when all else fails
    
- Seamless to the user — handled automatically
    

---

## TL;DR

|Term|Role|What it does|
|---|---|---|
|**STUN**|NAT detection tool|Tells you your public IP/port|
|**TURN**|Relay server|Middleman for traffic when STUN fails|
|**DERP**|Tailscale’s TURN system|Tailscale's encrypted relay fallback|