# Module 06: Vulnerability Scanning Commands

### 1. Nmap Scripting Engine (NSE)
Nmap is not just for scanning ports; it has built-in scripts to detect vulnerabilities.

| Command | Description | Use Case |
| :--- | :--- | :--- |
| `nmap --script vuln <target>` | Runs all vulnerability scripts | Fast check for the most common bugs. |
| `nmap --script http-enum <target>` | Enumerate common web files | Find `/phpmyadmin` or `/config`. |
| `nmap --script smb-vuln* <target>` | Check all SMB vulnerabilities | Look for EternalBlue or MS17-010. |
| `nmap --script-help <script>` | Get help for a specific script | Learn how to use a script. |

### 2. Automated Scanners
| Tool | Type | Focus |
| :--- | :--- | :--- |
| **Nessus** | Commercial | High accuracy, professional reporting. |
| **OpenVAS** | Open Source | Comprehensive, free alternative to Nessus. |
| **Nikto** | Web-specific | Fast, finds outdated web server configs. |

### The "Vulnerability Chain" (Example):
Find a service $\rightarrow$ Get version $\rightarrow$ Search for exploit $\rightarrow$ Verify with script:
```bash
nmap -sV <target> | grep "Apache 2.4.49" && nmap --script http-vuln-cve2021-41773 <target>
```
