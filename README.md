# LINUX_HARDENING
Notes and Steps to Harden and Secure Linux Environment. 
> Note: All commands were run from Windows Powershell using SSH into my Kali Linux VM.

---

## Hardening Steps Overview

### 1. Enabled Automatic Security Updates  
Installed and configured `unattended-upgrades` to automatically apply security patches and reduce vulnerability exposure. 
[See full details ->](./01-auto-updates)

---

### 2. Created a Non-root User with Sudo Access  
Instead of using the `root` account directly, I created a new user with sudo privileges to minimize risk if credentials are compromised.  
[See full details ->](./02-non-root-user)

---

### 3. Disabled Password Authentication for SSH  
Set up SSH key-based authentication and disabled password login to protect against brute-force SSH attacks.  
[See full details ->](./03-ssh-keys)

---

### 4. Harden SSH  
Moved SSH from the default port (22) to a custom port to reduce noise from automated scans and bots, and made additional SSH configuration changes for security. 
[See full details ->](./04-harden-ssh)

---

### 5. Configured UFW Firewall  
Enabled UFW (Uncomplicated Firewall) to allow only essential traffic (like SSH) and block everything else, including ICMP ping requests.  
[See full details ->](./05-ufw-firewall)

---

## Tools & Commands Used
- **User & Permissions:** `sudo adduser`, `sudo usermod -aG sudo yourusername`, `su - yourusername`  
- **System Updates:** `sudo apt update`, `sudo apt upgrade`, `sudo apt dist-upgrade`, `sudo apt install unattended-upgrades`, `sudo dpkg-reconfigure unattended-upgrades`,   
- **SSH Security:** `sudo systemctl restart sshd`, `ssh-keygen -b 4096`, `scp $env:USERPROFILE/.ssh/id_ed25519.pub kali@<server_ip>:~/.ssh/authorized_keys`, `ssh kali@<server-ip> -p <custom-port>`, `mkdir ~/.ssh && chmod 700 ~/.ssh`, `ssh-copy-id kali@<server_ip>`, `scp ~/.ssh/id_ed25519.pub kali@<server_ip>:~/.ssh/authorized_keys`, `sudo nano /etc/ssh/sshd_config`, `  
- **Firewall:** `sudo apt install ufw`, `sudo ufw allow <custom_port>`, `sudo ufw enable`, `sudo ufw status`, `sudo ss -tupln`  
- **Network Security:** custom UFW rules for ICMP (ping blocking)  
