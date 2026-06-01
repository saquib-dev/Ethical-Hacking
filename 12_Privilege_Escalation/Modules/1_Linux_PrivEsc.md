# Module 1: Linux Privilege Escalation

## What is PrivEsc?
Privilege Escalation is the process of moving from a low-privileged user (like `www-data`) to a high-privileged user (like `root`).

## Common Linux Paths to Root:
1. **Sudo Rights**: Some users can run specific commands as root without a password.
2. **SUID Binaries**: Special files that always run as the owner (often root). If the binary has a bug, you can escape it to a root shell.
3. **Kernel Exploits**: Using a CVE to exploit a bug in the Linux OS itself (like "Dirty Cow").
4. **Stored Passwords**: Finding passwords in config files, bash history, or `.ssh` keys.
