# Update Steps
The steps for performing manual and automatic updates in a Linux System.
## Manual
Run the following command to check for updates:
```bash
sudo apt update
```
You will be prompted to enter your password for sudo permissions. Afterwards, your output should look something like this:

<img width="752" height="234" alt="image" src="https://github.com/user-attachments/assets/38587b3f-cf08-43a6-a7fe-690c33415f6a" />

To install any available updates and manage dependencies, run:
```bash
sudo apt dist-upgrade
```
This may take a while depending on how many packages you need to install.
