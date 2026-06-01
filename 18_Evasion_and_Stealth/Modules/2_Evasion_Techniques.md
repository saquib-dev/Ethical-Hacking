# Module 2: Evasion Techniques

## Obfuscation
Changing the appearance of code without changing its function.
- **Encoding**: Using Base64 or XOR to hide strings.
- **Polymorphism**: Code that changes its own signature every time it runs.
- **Dead Code Insertion**: Adding useless instructions to confuse the analyzer.

## Bypassing the Shell
Traditional reverse shells (like `nc -e /bin/sh`) are immediately flagged.
- **Living off the Land (LotL)**: Using legitimate system tools (like `certutil`, `powershell`, `bash`) to perform malicious actions.
- **In-Memory Execution**: Running the payload directly in RAM without writing it to the disk (Fileless Malware).

## AMSI Bypass
The **Antimalware Scan Interface (AMSI)** in Windows scans PowerShell scripts in real-time. Bypassing AMSI is required for almost any modern Windows exploit.
