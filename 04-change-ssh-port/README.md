# 04-Change-SSH-Port
This section documents how to change the default SSH port in a Linux System.

## Why Change SSH Port?
- Changing the default SSH port **(22)** is a common security hardening step in Linux.

- While it doesn’t replace proper authentication methods **(like key-based login)**, it helps reduce unwanted noise from automated bots and scanners that constantly probe **port 22** for vulnerabilities. 

- By moving SSH to a non-standard port, you lower the number of brute-force attempts hitting your server, making logs cleaner and attacks less likely to succeed.

## What This Covers
- 
