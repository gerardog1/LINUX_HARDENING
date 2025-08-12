# SSH Key Pair Steps
The steps for creating, configuring, and securing SSH key pairs.

## Making Directory & Setting Permissions
Before anything, we have to run:
```bash
mkdir ~/.ssh && chmod 700 ~/.ssh
```
> Note: If the .ssh folder already exists, you still run the chmod 700 ~/.ssh command to ensure permissions are correct.


These are two commands seperated by the `&&` operator. 

*`mkdir ~/.ssh` — Creates a hidden directory called .ssh in the current user’s home folder. This is the standard location where SSH keys and configuration files are stored.*

*`chmod 700 ~/.ssh` — Sets the directory’s permissions so that only the owner can read, write, and execute inside it. This prevents other users from viewing or tampering with your SSH keys.*

SSH will refuse to use keys from a directory that is too open (e.g., readable by others). Setting 700 (read, write, execute only for the owner) is a security best practice and required for proper SSH authentication.

**Skipping the permission step is a common cause of the “Permissions are too open” error when using SSH keys.**

