---
tags:
  - VPN
  - Networking
---
**Link**: [[Wireguard]]

On the RouterOS, there are two menus for Wireguard:
- Wireguard: The actual Wireguard interface/tunnel
- Peers: The devices that are allowed to communicate through that interface


## 1- Create Wireguard Interface
Create an interface, with an arbitrary name like wg0.

You can specify a port. It will create your private key automatically.

## 2- Add Peer
```
Interface:       wg0
Public Key:      <Server WireGuard public key>
Endpoint:        REMOTE_IP:PORT
Allowed Address: 10.50.0.1/32 # remote IP of wireguard
Persistent Keepalive: 25s
```

If you are behind CGNAT, 'persistent keepalive' is useful for keeping connection alive

## 3- Add IP to the wg0 interface
Go to IP > Address > New

Add an IP to the wg0 interface. 

```
Address: 10.50.0.2/24
Interface: wg0
```

That's it.