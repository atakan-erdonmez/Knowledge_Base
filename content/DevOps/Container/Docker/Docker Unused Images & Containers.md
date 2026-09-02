- `docker container prune`: Delete all **stopped/exited** containers
- `docker image prune`: Delete the **dangling** images
- `docker image prune -a`: Delete all **unused** images, meaning images not linked to any active or stopped container
- `docker system prune`: Cleans up stopped containers, unused networks, and dangling images. Adding `--volume` also clears unattached storage volumes.


## Docker Image States
An image is a read-only template used to spawn containers.

- **In-Use:** The image is currently being used by at least one container—whether that container is **running or stopped**.
- **Unused:** The image has a valid tag (e.g., `ubuntu:latest`), but **zero** containers (running or stopped) are currently using it.
- **Dangling (`<none>:<none>`):** An image that has lost its name/tag. This usually happens when you pull an updated version of an image (like `:latest`). The tag moves to the new image, leaving the old layers tagged as `<none>`.