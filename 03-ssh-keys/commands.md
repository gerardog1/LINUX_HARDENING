# SSH Key Pair Steps
The steps for creating, configuring, and securing SSH key pairs.

## Making Directory & Setting Permissions
Before anything, we have to run:
```bash
mkdir ~/.ssh && chmod 700 ~/.ssh
```
> Note: If the .ssh folder already exists, you still run the chmod 700 ~/.ssh command to ensure permissions are correct.


These are two commands seperated by the `&&` operator. 

*`mkdir ~/.ssh` — Creates a hidden directory called .ssh in your current user’s home folder. This is the standard location where SSH keys and configuration files are stored.*

*`chmod 700 ~/.ssh` — Sets the directory’s permissions so that only the owner can read, write, and execute inside it. This prevents other users from viewing or tampering with your SSH keys.*

SSH will refuse to use keys from a directory that is too open (e.g., readable by others). Setting 700 (read, write, execute only for the owner) is a security best practice and required for proper SSH authentication.

**Skipping the permission step is a common cause of the “Permissions are too open” error when using SSH keys.**

## Create the Keys
Now logout of your Linux server, and go to your host machine's terminal. This is where we will be running the next command:
```bash
ssh-keygen -b 4096
```
> Note: This command will work on Mac, Linux, and Windows

*`-b 4096` tells SSH to generate an RSA key with 4096 bits of length, which is more secure than the older 2048-bit default. However, if your system defaults to `ed25519` keys, this option is ignored unless you explicitly choose RSA with `-t rsa.`*

After running the command, you’ll be prompted to choose where to save the key pair. 
<img width="569" height="52" alt="image" src="https://github.com/user-attachments/assets/7321e1cc-c9a8-48c2-a5c8-f66c149d2cac" />

Press Enter to accept the default location.

*By default, ssh-keygen saves the key in your `~/.ssh` directory and names it according to the key type used (for example, `id_ed25519` for ED25519 keys or `id_rsa` for RSA keys).*

*If you don’t specify a type with -t, the default key type depends on your OpenSSH version (ED25519 on most modern systems, RSA on older ones).*

If a key already exists at that location and you don’t want to overwrite it, type a different file name (e.g., `~/.ssh/id_ed25519_new`) to save it separately.

You will also be prompted to enter a passphrase, this is optional. 
> Note: A passphrase adds an extra layer of security by requiring it whenever the private key is used, but it’s not strictly necessary for every setup.

<img width="139" height="157" alt="image" src="https://github.com/user-attachments/assets/aa5fbdd4-937e-44d3-a210-55d9d5c9d5bd" />

Once complete, you’ll see confirmation that two files have been created — your private key and your public key — along with a visual fingerprint called randomart. This indicates your SSH key pair has been successfully generated.

Now when we navigate to the .ssh folder and list the contents, we will be able to see our public and private key. Run these commands:

**WINDOWS:**
```bash
cd .ssh
```
```bash
ls
```
> Note: LINUX/MAC OS use cd ~/.ssh

<img width="470" height="201" alt="image" src="https://github.com/user-attachments/assets/c6cbaea0-6cba-4308-9a5c-8c679fcf3d5c" />


My public key here is `id_ed25519.pub`, and my private is `id_ed25519`. 

If your keys are RSA, they will look something like: `id_rsa`, `id_rsa.pub`

## Share Public Key to Linux Server
Before we can send our public key from the host to our Linux server, we need to know the server’s IP address.

To do this, shut down your VM and change its network mode to Bridged Networking. In VirtualBox, you can do this by going to Settings > Network > Attached to: Bridged Adapter. Once you restart the VM, it will receive an IP address on your local network.

Run `ip a` inside the VM, look under `eth0`, and use whatever IP is listed as `inet` in your `SSH/scp` commands.”

Once you've found your ip, you're going to use it in the following command:

**WINDOWS**
```bash
scp $env:USERPROFILE/.ssh/id_ed25519.pub kali@<server_ip>:~/.ssh/authorized_keys
```
**LINUX**
```bash
ssh-copy-id kali@<server_ip>
```
**MAC OS**
```bash
scp ~/.ssh/id_ed25519.pub kali@<server_ip>:~/.ssh/authorized_keys
```
Your Linux Server now has your public key. Now you can ssh into your server without a password by using the secure key pair.

## How to SSH into Linux Server
Start your VM using your hypervisor (e.g., VirtualBox, VMware, Hyper-V). Make sure the VM is running before trying to SSH into it.

Go to your host terminal and run:
```bash
ssh kali@<server-ip>
```
At this point, you’ve successfully logged into your VM over SSH using your key pair. This completes the process of setting up a more secure, passwordless connection to your server.





