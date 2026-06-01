# Module 19: Reporting Lab

### Task 1: Building a Finding
1. Go back to one of your previous labs (e.g., Module 08 SQLi).
2. Write a professional "Technical Finding" for it using the template in `commands.md`.
3. Include a mocked-up "Proof of Concept" section.
4. Assign a CVSS score and justify it (e.g., "Critical because it allows full DB access").

### Task 2: Executive Summary
1. Imagine you just finished a pen-test of a small company. You found:
   - One SQL Injection (Critical).
   - One outdated Apache server (Medium).
   - No MFA on the VPN (High).
2. Write a 3-paragraph Executive Summary for the CEO. Focus on the **business risk**, not the technical details.

### Task 3: Evidence Organization
1. Create a folder structure for your evidence:
   - `/evidence/recon/`
   - `/evidence/exploitation/`
   - `/evidence/privesc/`
2. Organize your screenshots and log files into these folders.

### Task 4: Final Review
1. Review your report.
2. Ensure there is no sensitive data (like your own IP or clear-text passwords) that shouldn't be there.
3. Check that every "Critical" bug has a corresponding "Remediation" step.
