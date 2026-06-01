# Module 20: Final Project Lab Guide

### The Challenge: "Operation GlobalCorp"

**Objective**: Capture the flag on the Domain Controller.

### Guided Steps:
1. **The Perimeter**: Start with the web server. Find the vulnerability that lets you in.
2. **The Foothold**: Get a reverse shell. Stabilize it using `python3 -c 'import pty; pty.spawn("/bin/bash")'`.
3. **The Climb**: Escalate your privileges to root/SYSTEM.
4. **The Pivot**: Identify the internal network. Find the Domain Controller.
5. **The Roast**: Steal a service ticket via Kerberoasting. Crack it offline.
6. **The Crown**: Use the cracked credentials to move laterally. Use BloodHound to find the path to Domain Admin.
7. **The Win**: Forge a Golden Ticket or steal a Domain Admin token. Log into the DC.
8. **The Proof**: `cat C:\Flags\secret.txt`.

### Final Submission:
Create a final folder `C:\Users\salik\OneDrive\Desktop\Ethical hacking\final_report\` and include:
1. `Report.md` (The full professional report).
2. `/evidence/` (All screenshots and logs).
