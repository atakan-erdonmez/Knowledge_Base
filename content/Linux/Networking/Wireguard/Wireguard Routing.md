**Link**: [[Wireguard]]

For routing, you need to specify 'AllowedIPs' in the config file. Then, after applying, these routes will automatically be in the route table.

```
# AllowedIPs = 10.50.0.2/32, 192.168.10.0/24, 192.168.20.0/24, 192.168.30.0/24, 192.168.40.0/24

sudo wg-quick down wg0
sudo wg-quick up wg0   
```

Then, in `ip route` output, you will see the result.


For more info on [[Wireguard AllowedIPs]]