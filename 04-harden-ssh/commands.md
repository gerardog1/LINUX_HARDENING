# 04-Harden-SSH Steps
To begin hardening SSH, we need to edit its main configuration file: `sshd_config`. This file controls how the SSH service behaves, including which port it listens on, who can log in, and what authentication methods are allowed.

We use the `nano` text editor to open it:
```bash
sudo nano /etc/ssh/sshd_config
```

## SSH Hardening Changes
Once the file opens up, here's what you need to look for:

Navigate to where it says **`#Port 22`** (Port 22 is default)

**Delete the `#` to edit it**, and change the `22` to another number. 

Choose a new SSH port number between **1024–65535** that isn’t already in use, ideally a random and uncommon number to reduce automated attacks.

---

Now locate **"AddressFamily"** and change it from the default `any` to `inet`. 

This forces SSH to use only IPv4, which reduces the attack surface by disabling unnecessary IPv6 connections if you don’t need them.

---

Navigate to **"PermitRootLogin"** and change it from `yes` to `no`. 

This disables direct root logins over SSH, forcing users to authenticate with a normal account first and then escalate with sudo, which greatly reduces the risk of brute-force attacks and limits the damage if credentials are compromised.

---

Now go to **"PasswordAuthentication"** and change it from `yes` to `no`. 

This disables password-based logins, requiring SSH keys instead. This prevents brute-force attacks against user passwords and ensures only clients with a valid private key can connect.

Now hit `Ctrl+X`, `Y`, then `Enter` to save your changes.

---

After making changes to `sshd_config`, the SSH service must be restarted for the new settings to take effect. Without restarting, the server will continue running with the old configuration.

Run:
```bash
sudo systemctl restart sshd
```
> Safety Tip: Always keep your current SSH session open while testing a new one on the updated port. This way, if something goes wrong, you won’t be locked out of your server.

Open a new terminal window and try logging in using the updated port. This ensures the new configuration works before you close your original session.
```bash
ssh <username>@<server-ip> -p <custom-port> 
```
> Note: Without the `-p <custom-port>` option, SSH will default to port 22 and fail to connect. That’s exactly what we want — it means the server is no longer accepting connections on the default port.

**With these changes, SSH is now hardened: it uses a non-standard port, enforces key-based login, restricts root access, and only allows trusted users, creating a much more secure environment for remote administration.**
