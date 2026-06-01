# Module 20: Final Project - End-to-End Simulation

## 1. The Scenario
You have been hired as a penetration tester for "GlobalCorp". Your goal is to compromise the domain and steal the "Flag" (a secret file) located on the Domain Controller.

### The Target Environment:
- **Entry Point**: A public-facing web server (`web.globalcorp.local`).
- **Internal Network**: A subnet containing several workstations and a Domain Controller (`dc.globalcorp.local`).
- **Goal**: `C:\Flags\secret.txt` on the DC.

## 2. The Execution Workflow
You must apply everything you have learned in this course.

### Phase 1: Reconnaissance & Entry
1. **Nmap**: Scan the web server.
2. **Enum**: Find hidden directories (Gobuster) and vulnerabilities (Nikto).
3. **Exploit**: Use a web attack (SQLi, LFI, or XSS) to gain a shell.

### Phase 2: Post-Exploitation & PrivEsc
1. **Local Enum**: Check for SUID, Sudo, or Windows unquoted paths.
2. **PrivEsc**: Escalate to root/SYSTEM.
3. **Persistence**: Establish a permanent backdoor.

### Phase 3: Lateral Movement & AD Attack
1. **Internal Recon**: Use the shell to scan the internal network.
2. **AD Enum**: Find domain users and SPNs.
3. **Roasting**: Perform Kerberoasting to get a service account password.
4. **Pivot**: Use the service account to move to another machine.

### Phase 4: Domain Dominance
1. **BloodHound**: Map the path to Domain Admin.
2. **PrivEsc (AD)**: Use Pass-the-Hash or a Golden Ticket to become Domain Admin.
3. **The Prize**: Access the Domain Controller and read `secret.txt`.

## 3. Final Deliverable
The project is not complete until you produce a **Full Security Assessment Report** containing:
- Executive Summary.
- Technical findings for every step of the attack.
- Screenshots of the final flag.
- Remediation steps for the entire chain.
