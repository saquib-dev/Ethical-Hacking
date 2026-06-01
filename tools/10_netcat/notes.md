# Netcat (nc) - Notes

## Overview
Netcat, often referred to as the "TCP/IP Swiss Army Knife," is a versatile networking utility that reads and writes data across network connections using TCP or UDP protocols. It is a fundamental tool for network administrators, security professionals, and ethical hackers.

## Core Capabilities
- **Port Scanning:** Can be used for simple port scanning (though `nmap` is generally preferred).
- **Banner Grabbing:** Useful for identifying the service running on a specific port.
- **File Transfers:** Can easily transfer files between systems without needing FTP, SMB, or other protocols.
- **Backdoors/Shells:** Extremely popular for setting up reverse shells and bind shells during exploitation.
- **Port Forwarding/Relaying:** Redirecting traffic from one port or host to another.

## Security Considerations & Best Practices
- **Lack of Encryption:** Standard Netcat transmits data in plaintext, including passwords and shell commands. This makes it easily detectable by Intrusion Detection Systems (IDS) and network sniffers.
- **Modern Alternatives:** Tools like `Ncat` (part of the Nmap project) or `Socat` offer SSL/TLS encryption, making communications much more secure and harder to detect.
- **Detection:** Blue teams often monitor for `nc.exe` on Windows systems, as it is rarely used for legitimate administrative purposes in modern Windows environments.
