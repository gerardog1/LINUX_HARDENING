# UFW Firewall Steps
The steps for configuring and securing the server with UFW firewall.

## Check Ports in Use
Before we set up our firewall, we should check what ports are being used to determine what we'll allow into our server. Run the command:
```bash
sudo ss -tupln
```
- `ss`: A tool to show socket (network connection) information.
- `t`: Show TCP sockets.
- `u`: Show UDP sockets.
- `p`: Show the process using the socket.
- `l`: Show only listening sockets.
- `n`: Show numeric addresses/ports (instead of resolving names like "ssh").

<img width="1139" height="97" alt="image" src="https://github.com/user-attachments/assets/356f9152-8077-481c-b887-c60d7cce39dd" />

In my case, I have two open ports: UDP 546 used by NetworkManager (DHCPv6 client) and TCP 654 used by sshd (SSH server).

Since SSH is the only service we require for remote administration, we configured UFW to allow traffic only to that port. All other incoming connections remain blocked, while DHCPv6 continues to function safely as an outgoing client service.
## Install & Configure UFW
To install the UFW (Uncomplicated Firewall) Run:
```bash
sudo apt install ufw
```
By defualt the firewall isn't enabled yet. We'll take this moment to allow our custom SSH port. Run:
```bash
sudo ufw allow <custom_port>
```
Once rules are updated, you can now enable the UFW. Run:
```bash
sudo ufw enable
```
The UFW is now active, when we run `sudo ufw status` we should now see our allowed port.
```bash
sudo ufw status
```
<img width="482" height="156" alt="image" src="https://github.com/user-attachments/assets/e63a1854-f347-491c-89b4-6e1fc5c3d690" />

> Safety Tip: Always keep your current SSH session open and open a new terminal to test the connection on the port. This ensures your firewall rules are correct and prevents you from accidentally locking yourself out.

## Block Pings
Disabling ping responses makes your server less visible to automated scans and reduces the risk of being targeted, so it’s considered best practice to block them.

To block pings, run:
```bash
sudo nano /etc/ufw/before.rules
```
Once you're inside the file, locate the "**# ok icmp codes for INPUT**" section. 

You're going to add a **new** line of text, which is:
```bash
# Add this line to your firewall configuration file:
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP
```

It should look like this:

<img width="517" height="74" alt="image" src="https://github.com/user-attachments/assets/57c54443-f5a2-4ee5-b8fe-aeb30c6377e7" />

Hit `Ctrl+X, Y, Enter` to save changes.

Changes to the UFW ICMP rules may not take effect immediately, so rebooting ensures ping requests are blocked as expected:
```bash
sudo reboot
```

To check if pings are actually being blocked, run ping requests from your host machine to your server. If the results show "Request Timed Out", then you’ve successfully blocked pings.

<img width="310" height="108" alt="image" src="https://github.com/user-attachments/assets/801305ee-bd4f-4266-9bc6-6cc5aa11684c" />

---


**You’ve now applied foundational security measures by configuring UFW to control network traffic and disabling ICMP ping responses. These steps greatly reduce your server’s exposure to common attacks, forming a strong base for further hardening.**

