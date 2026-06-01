# Module 05: Enumeration Command Reference

### 1. SMB Enumeration (Windows)
| Command | Description | Use Case |
| :--- | :--- | :--- |
| `enum4linux -a <target>` | The "all-in-one" SMB tool | Gather users, shares, and OS info. |
| `smbclient -L \\\\<target>\\` | List available shares | Find folders like `\backups` or `\users`. |
| `smbclient \\\\<target>\\<share>` | Connect to a share | Access files if guest access is enabled. |
| `rpcclient -U "" <target>` | Use RPC to query users | Get a list of local users. |

### 2. Web Directory Enumeration
| Command | Description | Example |
| :--- | :--- | :--- |
| `gobuster dir -u <url> -w <list>` | High-speed directory brute-force | `gobuster dir -u http://target.com -w /usr/share/wordlists/dirb/common.txt` |
| `dirb <url>` | Simple directory scanner | `dirb http://target.com` |
| `nikto -h <url>` | Vulnerability scanner | Finds outdated software and risky files. |

### 3. DNS & Network Intelligence
| Command | Description | Example |
| :--- | :--- | :--- |
| `dnsrecon -d <domain>` | Comprehensive DNS enum | `dnsrecon -d company.com` |
| `dig axfr @<dns_server> <domain>` | Attempt Zone Transfer | `dig axfr @ns1.company.com company.com` |
| `whois <domain>` | Domain registration info | Find owner's email and phone number. |

### The "Enumeration Chain" (Example):
Find a hidden admin page and check it for vulnerabilities:
```bash
gobuster dir -u http://target.com -w common.txt | grep "admin" && nikto -h http://target.com/admin
```
