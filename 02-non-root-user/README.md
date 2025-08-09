# 02-Non Root User
This section details how to create non root users and add them into the sudo group.
## Why Create Non Root Users?
Logging into a root account directly presents a significant security risk due to the extensive permissions and potential for misuse or compromise.

A compromised root account allows an attacker to control the entire system, potentially leading to data breaches, system damage, and the installation of malware.

If an attacker compromises your account while you’re root, they immediately have unrestricted control.
## Why Add the User to the `sudo` Group?
By default, a new user account on many Linux distributions cannot run administrative commands.

The sudo group is a privileged group whose members can use the sudo command to temporarily gain root privileges for individual commands.

This allows you to:

Perform system administration without logging in as root.

Reduce risk — even if the user account is compromised, the attacker doesn’t automatically get root access unless they can also use sudo (and know your password).

Improve auditability — sudo logs each privileged command in /var/log/auth.log, so you know who ran what and when. Important in production environments.
## What This Covers
- Creating a new non-root user account.
- Assigning the new user to the `sudo` group for administrative privileges.
- Understanding the security benefits of using a non-root account for daily operations.
- Knowing when and why to fill out optional user information during account creation.
## Commands Used
See [Commands](./commands.md) for exact steps and terminal commands. 
