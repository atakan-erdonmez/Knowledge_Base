---
---
For creating a template in Proxmox, you will need a working VM first. You can create it using [[VM Creation with Cloud-init|Cloud-init]] or manually.

For templating, cloud-init installation is preferred, since when you clone, you won't need much change.



# Cloud-init 

Since it is installed with cloud-init, after cloning, you can specify all settings in the cloud-init drive. 

After you created with cloud-init, you can install the qemu-guest-agent to make cloning easier:

```
sudo apt update && sudo apt install -y qemu-guest-agent
sudo poweroff
```

# Manual

## Creation
```
sudo rm -f /etc/ssh/ssh_host_*
sudo truncate -s 0 /etc/machine-id
sudo ln -sf /etc/machine-id /var/lib/dbus/machine-id

sudo apt install qemu-guest-agent -y  
sudo apt clean && sudo apt autoremove -y        # Debian/Ubuntu
sudo dnf clean all && sudo dnf autoremove -y    # RHEL-based
sudo poweroff
```
- Delete ssh_host keys in /etc/ssh
- `sudo truncate -s 0 /etc/machine-id` OR i think you can echo "" to it.
- /var/lib/dbus/machine-id is a link to /etc/machine-id. Make sure it is soft link

**Suggestion**: I would suggest creating the template with main controller PC's public key on it. So you won't need to copy it again and again.


## First boot

```
sudo dpkg-reconfigure openssh-server       # Regenerates SSH host keys
sudo systemctl restart ssh
sudo hostnamectl set-hostname new-name
sudo reboot
```

- When you clone, it will copy the disk info as well. It will re-create the same sized disk.




# IMPORTANT
Cloud init only exist in VMs. It is used for  ssh key generation, for each vm to have seperate ssh keys.

In containers, you have to run the command:
`sudo dpkg-reconfigure openssh-server`

It re-creates the ssh keys