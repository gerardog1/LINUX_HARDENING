# 04-Harden-SSH
This section documents how to harden our SSH connections.

## Why Harden SSH?
- SSH is the primary method for remotely accessing and managing Linux servers. Securing it is critical to prevent unauthorized access.

- Hardening SSH involves reducing attack surfaces, enforcing strong authentication, and limiting access to trusted users.

- While changing the default SSH port can help reduce automated attacks, combining this with key-based login, disabling root access, and user restrictions ensures a much more secure SSH environment.

## What This Covers
- Changing the default SSH port (to reduce automated attack attempts).
- Disabling root login via SSH.
- Enforcing key-based authentication instead of password-based login.
- Restricting which users can SSH into the server.
- Adjusting SSH configuration (`/etc/ssh/sshd_config`) for better security.
- Restarting and testing the SSH service after changes.

## Commands Used
See [Commands](./commands.md) for exact steps and terminal commands.
