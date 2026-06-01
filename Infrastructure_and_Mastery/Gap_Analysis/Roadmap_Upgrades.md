# Roadmap Gap Analysis & Depth Updates

After reviewing the 20 phases, here are the "Depth Upgrades" you should apply to move from basic understanding to professional mastery.

## 1. Foundations (Phase 01) $\rightarrow$ Add "Scripting"
- **Current**: Basic commands.
- **Professional Upgrade**: Learn **Bash One-Liners**.
- **Task**: Practice using `grep`, `awk`, `sed`, and `cut` to filter large Nmap or WHOIS files. If you can't filter data, you'll be overwhelmed in real engagements.

## 2. Reconnaissance (Phase 02) $\rightarrow$ Add "OSINT Correlation"
- **Current**: Using tools in isolation.
- **Professional Upgrade**: Correlation.
- **Task**: Take a name from LinkedIn $\rightarrow$ Find an email via Hunter.io $\rightarrow$ Find that email's leaked passwords in a breach database $\rightarrow$ Use those passwords for a password spray attack.

## 3. Practical Exploitation (Phase 04) $\rightarrow$ Add "Payload Customization"
- **Current**: Using `msfvenom` defaults.
- **Professional Upgrade**: Understanding the payload.
- **Task**: Study the difference between a **Staged** and **Stage-less** payload. Learn why a staged payload is easier to detect.

## 4. Active Directory (Phase 13) $\rightarrow$ Add "GPO & ACLs"
- **Current**: Kerberoasting and BloodHound.
- **Professional Upgrade**: Group Policy Objects (GPO) and Access Control Lists (ACLs).
- **Task**: Learn how to find "Writeable GPOs" that allow you to push a malicious script to every computer in the domain.

## 5. Binary Exploitation (Phase 16) $\rightarrow$ Add "Heap/Stack Depth"
- **Current**: Basic Buffer Overflow.
- **Professional Upgrade**: Memory Corruption.
- **Task**: Study **ROP (Return Oriented Programming)**. In modern systems, the stack is non-executable (DEP/NX), so you must "borrow" code from the program itself to execute your attack.

## Summary of Necessary Mindset Shift:
**Stop asking: "What tool do I use?"**
**Start asking: "How does this system work, and where is the logic flaw?"**
