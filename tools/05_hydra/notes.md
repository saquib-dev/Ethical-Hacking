# Hydra Overview

## What is Hydra?
Hydra (THC-Hydra) is a very fast and flexible network logon cracker. Unlike offline crackers (like John the Ripper or Hashcat) that attempt to reverse cryptographic hashes, Hydra performs online brute-force or dictionary attacks against remote authentication services.

## How it Works
Hydra establishes network connections to a specified protocol (like SSH, FTP, HTTP, SMB, etc.) and attempts to authenticate using combinations of usernames and passwords. It analyzes the server's response to determine if the authentication was successful or failed.

## Supported Protocols
Hydra supports an extensive list of protocols, including:
- SSH, FTP, Telnet
- HTTP (Basic, Digest, Form POST/GET)
- SMB, RDP, VNC
- MySQL, PostgreSQL, MSSQL
- SMTP, POP3, IMAP
- LDAP, SNMP

## Best Practices & Considerations
- **Account Lockouts:** Be extremely careful when using Hydra against live targets. Many systems implement account lockout policies after a certain number of failed attempts. A careless Hydra attack can lock legitimate users out of the system.
- **Thread Tuning (`-t`):** Adjust the number of parallel tasks based on the service and network stability. Too many threads can crash the service (causing a DoS) or result in false negatives due to dropped connections.
- **Rate Limiting:** Network firewalls and intrusion prevention systems (IPS) will quickly detect and block aggressive Hydra attacks.
- **Stop on Success (`-f`):** Always use the `-f` flag to stop the attack as soon as a valid credential is found, saving time and reducing noise.
- **Use Targeted Lists:** Instead of using massive lists like `rockyou.txt` for online attacks, use smaller, targeted lists based on OSINT or gathered intelligence (e.g., default credentials for a specific device).
