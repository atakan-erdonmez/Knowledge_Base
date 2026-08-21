**Link**: [[Wireguard]]


## 1- Enable Port Forwarding Permanently
Sysctl is a Linux mechanism for viewing and changing kernel parameters at runtime.

```bash
sudo tee /etc/sysctl.d/99-wireguard-router.conf <<'EOF'
net.ipv4.ip_forward=1
EOF

sudo sysctl --system
```

Verify:
`sysctl net.ipv4.ip_forward`


## 2- Install Wireguard
```bash
sudo apt update && sudo apt install wireguard
wg --version
```

## 3- Generate Keys
Wireguard uses public and private keys for all peers for communication.

```bash
sudo su # need root to access the folder
cd /etc/wireguard

umask 077 # for making all files accessible by the root only

wg genkey | tee server_private.key | wg pubkey > server_public.key # create key, print to the server_private.key, create the pubkey from the file
```

Verify:
`cat /etc/wireguard/server_public.key`

## 4- Create Initial Wireguard Config
```bash
sudo nano /etc/wireguard/wg0.conf
```

Put:
```bash
[Interface]
Address = 10.50.0.1/24
ListenPort = 51820
PrivateKey = YOUR_PRIVATE_KEY
```

## 5- Enable 
We will use wg-quick, which is a wrapper around wg. wg is the low-level equivalent, which you would need to add routes, IPs, allowed hosts manually, like:
```bash
wg set wg0 listen-port 51820 private-key /path/to/private-key peer ABCDEF... allowed-ips 192.168.88.0/24 endpoint 209.202.254.14:8172
```
Then you would need to handle the linux networking separately etc. 

So instead, with wg-quick, it gets handled automatically.

Use the command:
```bash
sudo systemctl enable --now wg-quick@wg0
```

Verify:
```bash
sudo wg show
ip addr show wg0
```


## 6- Add Peers


---

For [[RouterOS Wireguard Installation]]