# Module 06: Vulnerability Analysis & Management

## 1. What is Vulnerability Analysis?
Once you know what services are running (Enumeration), you need to find **where they are weak**. Vulnerability Analysis is the process of identifying, quantifying, and prioritizing the vulnerabilities in a system.

### The Difference: Scanning vs. Analysis
- **Vulnerability Scanning**: Using a tool to find "known" bugs (CVEs). It is fast but produces "False Positives" (reporting a bug that isn't actually there).
- **Vulnerability Analysis**: A human reviewing the scan results, verifying them manually, and determining the actual risk to the business.

## 2. Understanding CVEs and CVSS
To speak the language of security, you must understand these two terms:

### CVE (Common Vulnerabilities and Exposures)
A unique ID given to a specific vulnerability in a software. 
*Example: **CVE-2017-0144** is the ID for the EternalBlue vulnerability in SMB.

### CVSS (Common Vulnerability Scoring System)
A numerical score (0.0 to 10.0) that tells you how dangerous a bug is.
- **0.1 - 3.9**: Low
- **4.0 - 6.9**: Medium
- **7.0 - 8.9**: High
- **9.0 - 10.0**: Critical (Must be fixed immediately!)

## 3. The Vulnerability Management Lifecycle
1. **Discovery**: Scan the network for assets and bugs.
2. **Prioritization**: Fix the "Critical" bugs on "Critical" servers first.
3. **Remediation**: Apply a patch, update the software, or change a configuration.
4. **Verification**: Re-scan to ensure the bug is gone.
