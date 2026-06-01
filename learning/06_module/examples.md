# Module 06: Practical Examples in Vulnerability Analysis

## 1. Translating a CVE to an Attack

During your enumeration phase, you discovered the target is running an older web framework. You search a vulnerability database (like Exploit-DB or the National Vulnerability Database) and find the following record:

**CVE-2021-44228 (Log4Shell)**
* **Description:** Apache Log4j2 JNDI features used in configuration, log messages, and parameters do not protect against attacker controlled LDAP and other JNDI related endpoints. An attacker who can control log messages or log message parameters can execute arbitrary code loaded from LDAP servers when message lookup substitution is enabled.
* **CVSS Score:** 9.8 (CRITICAL)

**What this means practically:**
Because the CVSS score is a 9.8, this is an incredibly dangerous bug. The description tells you that if you can force the web server to "log" a specific string of text (for example, typing a malicious payload into the "Username" field of a login box), the server will process that payload and execute your code, giving you full control of the machine.

## 2. Automated Vulnerability Scanning

Instead of looking up every version manually, ethical hackers often use automated tools like Nessus or Nmap's Scripting Engine (NSE) to find these CVEs quickly.

**Command (Using Nmap's Vulnerability Scripts):**
```bash
$ nmap -p 445 --script vuln 10.10.10.40
```

**Output:**
```text
PORT    STATE SERVICE
445/tcp open  microsoft-ds
| smb-vuln-ms17-010: 
|   VULNERABLE:
|   Remote Code Execution vulnerability in Microsoft SMBv1 servers (ms17-010)
|     State: VULNERABLE
|     IDs:  CVE:CVE-2017-0144
|     Risk factor: HIGH
|       A critical remote code execution vulnerability exists in Microsoft SMBv1...
```

## 3. Remediation and Reporting

As an ethical hacker, your job isn't just to find the bug; it's to help fix it. 

In your final report for the `ms17-010` (EternalBlue) vulnerability found above, your remediation advice would be:
1. **Immediate Action:** Disable SMBv1 across the network entirely, as it is a deprecated protocol.
2. **Patching:** Apply the Microsoft security update MS17-010 to the affected Windows machine.
3. **Verification:** Rerun the Nmap vulnerability scan post-patching to confirm the port is no longer vulnerable.
