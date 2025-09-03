# 03-SSH Keys
This section documents how to create public and private key pairs for secure SSH authentication.

## Why Create Key Pairs?
- Using SSH key pairs for authentication is significantly more secure than password-based logins. 

- Passwords can be guessed, stolen, or brute-forced, but SSH keys are cryptographic credentials that are virtually impossible to crack with current technology. 

- By storing the private key securely on your machine and only placing the matching public key on the server, you ensure that only a device in possession of that private key can log in — making unauthorized access far less likely.

## What This Covers
- Generating an SSH public and private key pair for secure authentication.

- Adding the public key to the server’s authorized keys.

- Ensuring only devices with the matching private key can access the server.

## Commands Used
See [Commands](./commands.md) for exact steps and terminal commands.
