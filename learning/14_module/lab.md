# Module 14: Windows PrivEsc Lab

### Task 1: Privilege Audit
1. Log into a Windows VM as a standard user.
2. Run `whoami /priv`.
3. If you see `SeImpersonatePrivilege` enabled, search for "PrintSpoofer" or "JuicyPotato" and attempt to gain SYSTEM access.

### Task 2: Unquoted Path Exploitation
1. Use the PowerShell command in `commands.md` to find an unquoted service path.
2. Check if you have write permissions to the folder (e.g., `C:\Program Files\`).
3. Use `msfvenom` to create a malicious `.exe` and name it to match the unquoted path (e.g., `My.exe`).
4. Upload the file and restart the service (if possible) or reboot the machine.

### Task 3: Automated Discovery
1. Upload `winpeas.exe` to the target.
2. Run it and analyze the output.
3. Find a "Critical" finding (highlighted in red).
4. Research the finding and use a corresponding exploit to reach SYSTEM.

### Task 4: Registry Hunting
1. Search the registry for passwords using `reg query`.
2. Look for keywords like "password", "admin", "pwd" in `HKEY_LOCAL_MACHINE`.
 la. If you find a password, try using it with `runas /user:administrator <cmd>`.
