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

## Create the Keys
Now logout of your Linux server, and go to your host machine's terminal. This is where we will be running the next command:
```bash
ssh-keygen -b 4096
```
> Note: This command will work on Mac, Linux, and Windows


*Generates a new SSH key pair with a length of 4096 bits, providing stronger encryption than the default 2048 bits and making it significantly more resistant to brute-force attacks.*

After running the command, you’ll be prompted to choose where to save the key pair. 
<img width="569" height="52" alt="image" src="https://github.com/user-attachments/assets/7321e1cc-c9a8-48c2-a5c8-f66c149d2cac" />

Press Enter to accept the default location.

By default, `ssh-keygen` suggests saving the key in your `~/.ssh` directory, with the filename based on the key type you choose (for example, id_ed25519 for ED25519 keys).

If a key already exists at that location and you don’t want to overwrite it, type a different file name (e.g., ~/.ssh/id_ed25519_new) to save it separately.

You will also be prompted to enter a passphrase, this is optional. 

A passphrase adds an extra layer of security by requiring it whenever the private key is used, but it’s not strictly necessary for every setup.

Once complete, you’ll see confirmation that two files have been created — your private key and your public key — along with a visual fingerprint called randomart. This indicates your SSH key pair has been successfully generated.

Now when we navigate to the .ssh folder and list the contents, we will be able to see our public key. Run these commands:
WINDOWS
```bash
cd .ssh
```
```bash
ls
```
> Note: LINUX/MAC OS use cd ~/.ssh

