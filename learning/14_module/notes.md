# Module 14: Windows Privilege Escalation (PrivEsc)

## 1. Windows PrivEsc Overview
Windows privilege escalation is often more complex than Linux due to the way permissions (ACLs) and Tokens are handled. The goal is usually to move from a standard user to **SYSTEM** (the highest authority).

## 2. Common Windows Vectors

### A. Unquoted Service Paths
If a service path contains spaces and is not wrapped in quotes, Windows will try to guess the path.
- **Example**: `C:\Program Files\My App\service.exe`
- Windows will try to run:
  1. `C:\Program.exe`
  2. `C:\Program Files\My.exe`
- If you can write a malicious `My.exe` in `C:\Program Files\`, the service will run it as SYSTEM.

### B. Token Impersonation (Juicy Potato)
Windows uses tokens to manage permissions. Certain services (like BITS) run with higher privileges. "Potato" attacks trick these services into authenticating to the attacker, allowing the attacker to steal a SYSTEM token.

### C. Insecure Registry Keys
Many applications store sensitive data or paths in the Registry. If a low-privilege user can write to a key that is read by a SYSTEM service, they can redirect the service to run a malicious file.

### D. Password in Files
Many Windows administrators leave passwords in:
- `Unattend.xml` (used for automated installs).
- Registry keys (`HKLM\SOFTWARE\Microsoft...`).
- Configuration files (web.config, settings.ini).

## 3. The Windows Privilege Hierarchy
- **Guest**: Lowest.
- **User**: Standard access.
- **Administrator**: High access, but limited by **UAC (User Account Control)**.
- **SYSTEM**: Absolute control over the OS.
