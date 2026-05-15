---
tags:
  - Networking
  - Security
  - Network_Sec
created: 2026-03-30T09:43
updated: 2026-03-30T09:43
---

/etc/proxychains -> config file

proxy_dns -> dns over proxy

it goes through proxies from the top of the file

`proxychains program`


# How to Install
```
sudo apt install shadowsocks-libev
```

ss-local -s YOUR_SERVER_IP -p SERVER_PORT -k YOUR_PASSWORD -m aes-256-gcm -l 1080
