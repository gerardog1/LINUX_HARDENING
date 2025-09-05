# LINUX_HARDENING
Notes and Steps to Harden and Secure Linux Environment 
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
Moved SSH from port 22 to a custom port using port forwarding to reduce noise from automated scans and bots. As well as making changes to our SSH settings.  
[See full details ->](./04-harden-ssh)

---

### 5. Configured UFW Firewall  
Enabled UFW (Uncomplicated Firewall) to allow only essential traffic (like SSH) and block everything else, including ICMP ping requests.  
[See full details ->](./05-ufw-firewall)

---

## Why I Did This

I'm currently studying for the CompTIA Security+ certification and wanted hands-on practice with real-world Linux security techniques. This is just the start.  
These hardening steps helped me:
- Understand secure system configuration
- Apply the principle of least privilege
- Practice safe remote access techniques
- Reduce my system’s attack surface

---

## Tools & Commands Used
- `adduser`, `usermod`, `sudo`, `nano`, `-tupln`
- `apt`, `unattended-upgrades`
- `ufw`, `status`, `enable`
- `sshd_config`, `systemctl`, `ssh-keygen`
- `scp`, `ssh`, `port forwarding`, `ss`

---

## Next Steps 
- Configure `fail2ban` for intrusion detection
- Set up logging and alerts
- Explore `auditd` for file monitoring
- Document full recovery/backup plan
- Explore and Learn a `SIEM` tool.
- Incident Response
- Higher Level Hardening
