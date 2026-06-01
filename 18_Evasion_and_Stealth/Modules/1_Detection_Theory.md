# Module 1: Understanding Detection

## How AV/EDR Works
Modern security software doesn't just look for "files"; they look for **Behavior**.
- **Signature-Based**: Looks for a specific hash of a known virus. (Easy to bypass).
- **Heuristic-Based**: Looks for "suspicious" patterns (e.g., a program that tries to inject code into `lsass.exe`).
- **Behavioral Analysis**: Monitors the system for weird activity (e.g., a Word document suddenly starting a PowerShell session).

## The Cat and Mouse Game
As soon as a security company finds a way to detect an exploit, hackers find a way to "wrap" or "obfuscate" the exploit to make it look like a normal program.
