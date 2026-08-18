---
tags:
  - ai
  - ollama
---
Open WebUI is a feature-rich, web-based frontend designed to centralize and visualize your AI workflows. It mimics premium cloud interfaces (like ChatGPT) and connects seamlessly to local engines like Ollama as well as external cloud APIs. 

Because the backend Ollama engine already manages model weight loading directly from your secondary SSD, the Open WebUI container can remain completely stateless and streamlined—it only requires a single light volume to store its own application data like chat logs, user accounts, and custom prompts.

### Option A: Running with Docker (Standard)

This command runs Open WebUI via Docker in detached mode, exposing it on host port 3000, and uses the `--add-host` network bridge flag to safely pass prompts to your host-managed Ollama API.


```bash
sudo docker run -d \
  -p 3000:8080 \
  --add-host=host.docker.internal:host-gateway \
  -v open-webui:/app/backend/data \
  --name open-webui \
  --restart always \
  ghcr.io/open-webui/open-webui:main
```

### Option B: Running with Rootless Podman (Recommended for Fedora)

Since Fedora features native, daemonless Podman support, you can drop `sudo` entirely. The container runs safely within your user-space, shifting the network bridge target to `host.containers.internal`.


```bash
podman run -d \
  -p 3000:8080 \
  --name open-webui \
  --add-host=host.containers.internal:host-gateway \
  -v open-webui:/app/backend/data \
  --restart always \
  ghcr.io/open-webui/open-webui:main
```

### Option C: Declarative Deployment (Podman / Docker Compose)

To avoid copy-pasting long, multi-line terminal commands, save the configuration as a `compose.yaml` file to start and stop the environment declaratively.


```yaml
services:
  open-webui:
    image: ghcr.io/open-webui/open-webui:main
    container_name: open-webui
    ports:
      - "3000:8080"
    extra_hosts:
      - "host.containers.internal:host-gateway"
    volumes:
      - open-webui:/app/backend/data
    restart: always

volumes:
  open-webui:
```

- **To enable podman socket:** `systemctl --user enable --now podman.socket`
- **To start the container:** `podman compose up -d`
- **To stop the container:** `podman compose down`