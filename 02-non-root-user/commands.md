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
You will be prompted to enter your password for sudo if you're not already root, then it will ask you to create a new password for the new user. Once you've made one and press enter, the following should appear:

<img width="361" height="213" alt="image" src="https://github.com/user-attachments/assets/45fa6fff-a473-4021-be30-f4e0ab413d3f" />

> For this hardening project, **these fields were skipped** by pressing Enter because they are not required for functionality.
In production environments, these details can be valuable for:

***Auditing** – linking accounts to specific individuals.*

***Helpdesk support** – providing contact info for account owners.*

***Compliance requirements** – some organizations require user metadata for policy or legal reasons.*

If these fields are not needed, they can be left blank without impacting account creation. Press Enter or type `y` then enter to complete user creation.

## Add User to Sudo Group
Now that we've created our new user, we can add it to the sudo group by running the following command:
```bash
sudo usermod -aG sudo yourusername
```
