# Module 05: Service Enumeration & Intelligence Gathering

## 1. What is Enumeration?
If Scanning is like finding an open door, **Enumeration** is like looking through the window to see what's inside the room. It is the process of establishing an active connection to the target to discover more detailed information.

### The Goals of Enumeration:
- **Usernames**: Find valid users for password attacks.
- **Network Shares**: Find open folders (SMB) that might contain sensitive data.
- **Service Versions**: Get the exact version of a software (e.g., Apache 2.4.18) to find a specific exploit (CVE).
- **Directory Structure**: Find hidden pages on a website (e.g., `/admin` or `/config.php`).

## 2. Common Targets for Enumeration

### SMB (Server Message Block) - Port 445
SMB is used for file and printer sharing in Windows. It is one of the most exploited services in history (e.g., EternalBlue).
- **Null Sessions**: Trying to connect without a username/password.

### HTTP/HTTPS (Web) - Port 80/443
Web servers often hide sensitive directories or use outdated plugins.
- **Directory Brute-forcing**: Guessing common folder names using a wordlist.

### DNS (Domain Name System) - Port 53
Attackers try to find "Subdomains" (e.g., `dev.company.com`, `vpn.company.com`) to expand their attack surface.
- **Zone Transfer (AXFR)**: A misconfigured DNS server might give away the entire DNS record list.

### SNMP (Simple Network Management Protocol) - Port 161
Used to monitor network devices. If the "Community String" (password) is default (`public`), an attacker can see everything about the device.
