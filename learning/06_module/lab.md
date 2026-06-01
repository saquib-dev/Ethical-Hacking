# Module 06: Vulnerability Analysis Lab

### Task 1: NSE Scripting
1. Use `nmap --script vuln <target>` against a vulnerable VM.
2. Identify one vulnerability found. Copy the **CVE ID** (e.g., CVE-2017-xxxx).
3. Go to [cve.mitre.org](https://cve.mitre.org) and search for that ID.
4. Read the description: What software is affected? What is the impact (Remote Code Execution, Denial of Service)?

### Task 2: Professional Scanning with Nessus
1. Install **Nessus Essentials** on your Kali VM.
2. Create a "Basic Network Scan" and target your lab network.
3. Once the scan is complete, filter the results by **"Critical"** severity.
4. Select one critical finding and read the "Remediation" section. How would you fix this bug in a real company?

### Task 3: False Positive Verification
1. Find a "Medium" vulnerability reported by a tool.
2. Try to verify it manually (e.g., if it says a directory exists, try to visit it in a browser).
3. If you cannot find it, mark it as a **False Positive** and document why.
