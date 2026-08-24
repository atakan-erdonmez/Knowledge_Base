**Link**: [[00_KnowledgeBase/Linux/Linux|Linux]]

1. **Establish a Plan B Console Session**
    - _What:_ Connect via your hosting provider's panel before editing configurations.
    - _Why:_ Bypasses SSH so you can regain access if you get locked out.
2. **Update the System Packages**
    - _What:_ Run package manager security updates.
    - _Debian/Ubuntu Code:_ `sudo apt update && sudo apt dist-upgrade -y`
    - _Fedora/RHEL Code:_ `sudo dnf update -y`
3. **Set Unique Hostname via Systemd**
    - _What:_ Assign a clear hostname using systemd.
    - _Code:_ `sudo hostnamectl set-hostname <server-name>`
4. **Configure Local Resolution**
    - _What:_ Map your server hostname locally.
    - _Code:_ Edit `/etc/hosts` and add `127.0.1.1 <server-name>`
5. **Create standard Non-Root User**
    - _What:_ Create a normal user for everyday administration.
    - _Debian/Ubuntu Code:_ `sudo adduser <username>`
    - _Fedora/RHEL Code:_ `sudo useradd -m -g users -G wheel <username> && sudo passwd <username>`
6. **Configure Administrative Privileges (Sudo)**
    - _What:_ Grant sudo command rights to your user.
    - _Debian/Ubuntu Code:_ `sudo usermod -aG sudo <username>`
7. **Transfer Public Key**
	- _What:_ Copy your public key file to the remote server.
	- _Code (Local):_ `ssh-copy-id -i ~/.ssh/id_ed25519.pub <username>@<server-ip>`
8. **Verify Key Login Natively**
    - _What:_ Log in using your key without typing account passwords.
    - _Code (Local):_ `ssh <username>@<server-ip>`
9. **Harden the SSH Configuration**
    - _What:_ Edit `/etc/ssh/sshd_config` to secure credentials.
    - _Code:_ Set `PermitRootLogin no` and `PasswordAuthentication no`
10. **Restart & Inspect the SSH Daemon**
    - _What:_ Restart the daemon to load settings into memory.
    - _Debian/Ubuntu Code:_ `sudo systemctl restart ssh && sudo systemctl status ssh`
    - _Fedora/RHEL Code:_ `sudo systemctl restart sshd && sudo systemctl status sshd`
11. **Secondary-Window Safety Test**
    - _What:_ Attempt to log in via a fresh terminal window while keeping your active session alive.
    - _Code (Local):_ `ssh <username>@<server-ip>`
12. **System Reboot**
    - _What:_ Fully restart the machine to commit the kernel upgrades and hostnames.
    - _Code:_ `sudo reboot`