# Update Steps
The steps for performing manual and automatic updates in a Linux System.
## Manual
Run the following command to check for updates:
```bash
sudo apt update
```
You will be prompted to enter your password for sudo permissions.

Afterwards, your output should look something like this:

<img width="496" height="76" alt="image" src="https://github.com/user-attachments/assets/7fb91d50-ae0b-4a81-a83e-88d96dacd915" />

*This updates the list of available packages and versions from the repositories.* 

To install any available updates and manage dependencies, run:
```bash
sudo apt dist-upgrade
```
*This command goes beyond a simple upgrade by intelligently handling changes in package dependencies, potentially installing new packages or removing obsolete ones to resolve conflicts and ensure a smooth upgrade process.* 

This may take a while depending on how many packages you need to install. 

---

## Automatic
To enable automatic updates in Linux, start with running the following command:
```bash
sudo apt install unattended-upgrades
```
*This command installs the package `unattended-upgrades` that enables automatic security updates on the system.*
> Note: You will be prompted to continue [Y/n] Type y and press enter.


Once it's done installing, we're going to reconfigure the `unattended-upgrades` package by running:
```bash
sudo dpkg-reconfigure unattended-upgrades
```
> –priority=low is optional here since unattended-upgrades only has one debconf question.


*This command prompts us with a question to enable automatic updates as seen below:*
<img width="843" height="253" alt="image" src="https://github.com/user-attachments/assets/df1084db-8803-442d-bb09-15d590c7ba81" />

Select Yes, press Enter, and you're done.

**Automatic updates are now enabled, ensuring your system stays up to date with the latest security patches and improvements without manual intervention.**
