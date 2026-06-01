# Module 14: Windows PrivEsc Commands

### 1. Basic Enumeration
| Command | Description | Use Case |
| :--- | :--- | :--- |
| `whoami /priv` | List user privileges | Check for `SeImpersonatePrivilege`. |
| `systeminfo` | System info | Check OS version and patches. |
| `net user` | List all users | Find targets for password attacks. |
| `net localgroup administrators` | List admin users | See who has the keys to the kingdom. |

### 2. Finding Unquoted Service Paths
Use this PowerShell command to find vulnerable services:
```powershell
wmic service get name,displayname,pathname,startmode | findstr /i "Auto" | findstr /i /v "C:\Windows\\" | findstr /i /v """
```

### 3. Automation Tools
| Tool | Description | Use Case |
| :--- | :--- | :--- |
| **WinPEAS** | Windows PrivEsc Awesome Scripts | The gold standard for Windows enum. |
| **PowerUp.ps1** | PowerShell PrivEsc script | Specifically finds misconfigurations. |
| **PrivescCheck** | Bash script for Windows | Lightweight enumeration. |

**Running WinPEAS:**
1. Upload `winpeas.exe` to the target.
2. Execute: `winpeas.exe`

### 4. Exploiting SUID-like Permissions
If you have write access to a service executable, simply replace it with your payload (e.g., a reverse shell) and restart the service:
`sc stop <service_name>` $\rightarrow$ `sc start <service_name>`
