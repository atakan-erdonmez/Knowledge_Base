When you have a .env file in your brain node that you need to read but don't want to copy, you can use the code below. 

It is an example of cloudflare tunnel token.

deploy.yaml:
```yaml
- name: test
	vars:
		cloudflared_token: "{{ lookup('ini', 'CLOUDFLARED_TOKEN type=properties file=.env') }}"
```


compose.yaml
```yaml
command: tunnel --no-autoupdate run --token {{ cloudflared_token }}
```

.env:
```
CLOUDFLARED_TOKEN=token_here
```

You need to use 'lookup' plugin for Ansible, and use Jinja2 templating in the file.

> [!WARNING]
>  You should **NOT** use copy command. Instead use **template** for this to work.

