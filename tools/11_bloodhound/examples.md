# BloodHound Examples

## Scenario: Auditing Active Directory Permissions
BloodHound is used to map out Active Directory environments to visually identify complex, unintended privilege escalation paths. Data is typically first gathered using an ingestor like SharpHound.

**Command (Data Collection using SharpHound):**
```powershell
Invoke-BloodHound -CollectionMethod All -Domain corp.local -ZipFileName AD_Audit.zip
```

**Mocked Output:**
```text
[+] Initializing SharpHound at 09:00:00
[+] Resolving Domain... corp.local
[+] Starting Collection...
[+] Collecting Sessions
[+] Collecting Local Admin
[+] Finishing Collection...
[+] Zipping data to AD_Audit.zip
```

**Explanation:**
- `-CollectionMethod All`: Specifies that all available data collection methods should be run (e.g., Group memberships, Local Admins, Sessions, Object Properties).
- `-Domain corp.local`: The target domain to audit.
- `-ZipFileName AD_Audit.zip`: The name of the output zip archive containing the JSON data, which can then be imported into the BloodHound GUI for visual graph analysis.
