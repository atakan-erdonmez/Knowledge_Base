| What you want               | Command                       |
|-----------------------------|-------------------------------|
| Current SMART info / health | smartctl -a /dev/sda          |
| Quick overall health only   | smartctl -H /dev/sda          |
| SMART attributes only       | smartctl -A /dev/sda          |
| Start short test            | smartctl -t short /dev/sda    |
| Start long/full test        | smartctl -t long /dev/sda     |
| Check test progress         | smartctl -a /dev/sda          |
| See test results/history    | smartctl -l selftest /dev/sda |
| See SMART error log         | smartctl -l error /dev/sda    |
| Cancel running test         | smartctl -X /dev/sda          |
