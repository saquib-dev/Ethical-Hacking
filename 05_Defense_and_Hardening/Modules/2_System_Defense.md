# Module 2: System Defense

## Hardening a System
Hardening means removing everything you don't need to reduce the "Attack Surface".

## Key Hardening Steps:
1. **Disable Unused Services**: If you don't need FTP, turn it off. One less door for a hacker.
2. **Strong Passwords & MFA**: Multi-Factor Authentication (MFA) makes a stolen password useless.
3. **Patching**: Keep software updated. Updates often fix the CVEs you searched for earlier.
4. **Principle of Least Privilege**: Users should only have the permissions they absolutely need. No one should use "Root" for daily tasks.

## IDS/IPS (Intrusion Detection/Prevention)
Tools like **Snort** or **Suricata** watch network traffic for "signatures" of attacks and alert the admin or block the IP automatically.
