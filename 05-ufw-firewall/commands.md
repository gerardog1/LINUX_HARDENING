# UFW Firewall Steps
The steps for configuring and securing the server with UFW firewall.

## Check Ports in Use
Before we set up pur firewall, we should check what ports are being used to determine what we'll allow into our server. Run the command:
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

