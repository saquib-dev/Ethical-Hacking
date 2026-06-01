# Module 2: Windows Privilege Escalation

## Getting SYSTEM Access
In Windows, the highest level of access is `NT AUTHORITY\SYSTEM`.

## Common Windows Paths:
1. **Unquoted Service Paths**: A flaw in how Windows handles spaces in folder names, allowing you to replace a service executable.
2. **Kernel Exploits**: Exploiting the Windows Kernel.
3. **Stored Credentials**: Finding passwords in the Registry or using tools like `Mimikatz` to pull passwords from memory.
4. **Wrong Permissions**: Finding a folder where a low-user can write files that a high-user executes.
