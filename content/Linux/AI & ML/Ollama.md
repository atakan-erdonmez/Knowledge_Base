---
created: 2026-03-30T09:43
updated: 2026-03-30T09:43
tags:
  - ai
  - ollama
---
Ollama is a lightweight, open-source runtime engine that allows you to run large language models locally. It acts as a background service that manages model weights, parameters, and tokenization, utilizing system hardware acceleration (such as AMD ROCm or NVIDIA CUDA) to perform high-speed tensor calculations entirely on your machine. It exposes a local API endpoint on port `11434` which client interfaces and developer tools use to stream completions.

### Basic CLI Commands

- `ollama serve` -> Manually starts the background Ollama server engine.
- `ollama pull <model>` -> Downloads a specified model from the Ollama registry without launching a chat session.
- `ollama run <model>` -> Loads the specified model into memory and launches an interactive chat session directly inside your terminal.
- `ollama list` -> Lists all downloaded models currently available on your local system.
- `ollama ps` -> Displays which models are currently loaded active into your GPU VRAM or system RAM.

### Service & External SSD Storage Configuration

To prevent multi-gigabyte models from filling up the main operating system drive, the storage path is offloaded to a secondary dedicated SSD mounted at `/mnt/llm_storage`. This is managed via systemd configurations:

- **Base Service Configuration (`/etc/systemd/system/ollama.service`):** Defines core service properties, binds the engine to run under a restricted `ollama` user profile, and opens the host network boundary (`OLLAMA_HOST=0.0.0.0:11434`) to accept outside traffic from local containers.
    
- **Storage Path Drop-in Override (`/etc/systemd/system/ollama.service.d/override.conf`):** Overrides the base environment values safely without touching the core package file. It points model downloads directly to the secondary SSD:

    ```ini
    [Service]  
    Environment="OLLAMA_MODELS=/mnt/llm_storage"
    ```


## UI
[[OpenWebUI]]



