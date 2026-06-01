# Module 12: The Metasploit Framework (MSF)

## 1. What is Metasploit?
Metasploit is the most widely used penetration testing framework in the world. Instead of manually writing exploits, MSF provides a massive database of pre-written exploit code, payloads, and scanners.

## 2. Key Components of MSF

### A. msfconsole
The main interactive command-line interface. This is where you search for exploits and launch attacks.

### B. Exploits
The "delivery vehicle". An exploit is a piece of code that takes advantage of a vulnerability (e.g., a buffer overflow) to get inside the system.

### C. Payloads
The "payload" is the code that runs **after** the exploit succeeds.
- **Staged Payloads**: A small "stager" is sent first, which then downloads the larger "stage" (e.g., `windows/x64/meterpreter/reverse_tcp`).
- **Non-Staged Payloads**: The entire payload is sent at once (e.g., `windows/x64/shell_reverse_tcp`).

### D. Meterpreter
The "Gold Standard" of payloads. Meterpreter is an advanced, multi-functional shell that lives in the target's memory. It allows you to:
- Upload/Download files.
- Dump password hashes.
- Take screenshots or record the microphone.
- Pivot to other machines on the network.

### E. msfvenom
A standalone tool used to generate custom payloads (e.g., creating a `.exe` or `.apk` file that connects back to your machine).

## 3. The MSF Workflow
1. **Search**: Find an exploit for the service version you found during enumeration.
2. **Select**: Choose the exploit module.
3. **Configure**: Set the `RHOSTS` (Target IP) and `LHOST` (Your IP).
4. **Exploit**: Launch the attack.
