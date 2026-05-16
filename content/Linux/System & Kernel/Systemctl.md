---
created: 2026-03-30T09:43
updated: 2026-05-16T17:41
---
- systemctl get-default : show the target (state)
- systemctl isolate “multi-user.target” : switch to that specific target
- systemctl set-default : switch to specific target at reboot/default
- `systemctl cat` 

```
systemctl list-units --type=service --state=running

state enable,generated, running
```


systemctl daemon-reload -> reload systemd related settings

/etc/systemd/system/ -> service files

~/.config/systemd/user -> user level systemd fikles

### List All Services

To see only your user .service units:
Run:

`systemctl --user list-unit-files --type=service`
This shows just user services that are:

- Defined
- Enabled/disabled
- Located in:
	- ~/.config/systemd/user/
	- /etc/systemd/user/
	- /usr/lib/systemd/user/ (from packages)