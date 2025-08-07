# Update Steps
The steps for performing manual and automatic updates in a Linux System.
## Manual
Run the following command to check for updates:
```bash
sudo apt update
```
You will be prompted to enter your password for sudo permissions. Afterwards, your output should look something like this:

<img width="496" height="76" alt="image" src="https://github.com/user-attachments/assets/7fb91d50-ae0b-4a81-a83e-88d96dacd915" />

*This updates the list of available packages and versions from the repositories.* To install any available updates and manage dependencies, run:
```bash
sudo apt dist-upgrade
```
This may take a while depending on how many packages you need to install. *This command goes beyond a simple upgrade by intelligently handling changes in package dependencies, potentially installing new packages or removing obsolete ones to resolve conflicts and ensure a smooth upgrade process.*
