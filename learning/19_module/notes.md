# Module 19: Reporting and Documentation

## 1. Why Reporting Matters
A penetration test is useless if the client doesn't know how to fix the bugs. The report is the only "product" the client actually pays for.

### Goals of a Security Report:
- **For Executives**: A high-level summary of the risk (Business impact).
- **For Technical Staff**: A detailed, step-by-step guide to reproducing the bug.
- **For Compliance**: Proof that the company is following security standards (e.g., PCI-DSS, HIPAA).

## 2. The Structure of a Professional Report

### A. Executive Summary
- **Overall Risk Score**: (e.g., Critical, High, Medium, Low).
- **Key Findings**: "We found that your internal database is exposed to the internet."
- **Recommendations**: "Implement Multi-Factor Authentication (MFA)."

### B. Technical Findings (The Core)
For every bug found, include:
- **Title**: (e.g., "Unauthenticated Remote Code Execution in Apache").
- **Severity**: (Critical/High/Medium/Low).
- **CVE ID**: (If applicable).
- **Description**: What is the bug?
- **Proof of Concept (PoC)**: Step-by-step instructions and **screenshots**.
- **Impact**: "An attacker could steal all customer credit card data."
- **Remediation**: How to fix it (e.g., "Update to Apache version 2.4.50").

### C. Appendices
- List of all tools used.
- List of all IP addresses tested.
- Full Nmap scan results.

## 3. Evidence Collection
If you can't prove it, it didn't happen.
- **Screenshots**: Always capture the payload and the result.
- **Logs**: Save the output of your terminal.
- **Hashes**: Document the hashes of any files you uploaded to the system.
