# Non Root Sudo User Steps
> Note: If you are already logged in as root, using sudo is rudundant and you can simply type the command that follows it.

If your shell prompt ends in a `#` , you are logged in as the root user.
If your shell prompt ends in a `$` , you are logged in as a regular user.

---

## Create New User
The first step is to add a new user. Type or paste this command then type a username of your choice at the end:
```bash
sudo adduser
```
*Your command should look something like this: `sudo adduser yourusername`.*
You will be prompted to enter your password for sudo if you're not already root, then it will ask you to create a new password for the new user. Once you've made one and pressed enter, the following should appear:

<img width="361" height="213" alt="image" src="https://github.com/user-attachments/assets/45fa6fff-a473-4021-be30-f4e0ab413d3f" />

> For this hardening project, **these fields were skipped** by pressing Enter because they are not required for functionality.
In production environments, these details can be valuable for:

***Auditing** – linking accounts to specific individuals.*

***Helpdesk support** – providing contact info for account owners.*

***Compliance requirements** – some organizations require user metadata for policy or legal reasons.*

If these fields are not needed, they can be left blank without impacting account creation. Press Enter or type `y` then enter to complete user creation.

## Add User to Sudo Group
Now that you've created a new user, you can add it to the sudo group by running the following command:
```bash
sudo usermod -aG sudo yourusername
```
*Adds your new user to the sudo group, giving it permission to run commands with administrative (root) privileges when needed.*
If you’re using a graphical interface, you can switch to the new user by logging out and then logging back in with the new username and password. Alternatively you can also run the following command:
```bash
su - yourusername
```
It will switch you to the new user account right there in the terminal without logging out or closing anything.

You’ll just need to enter the new user’s password when prompted.
