# Module 19: Reporting Commands

### 1. Documentation Tools
| Tool | Use Case | Note |
| :--- | :--- | :--- |
| **CherryTree** | Hierarchical Note Taking | Great for organizing a pen-test. |
| **Obsidian** | Knowledge Base | Using Markdown for fast documentation. |
| **KeepassXC** | Password Management | Store all stolen credentials securely. |
| **Screenshots** | Evidence | Use `Flameshot` or `Snipping Tool`. |

### 2. Formatting Findings
Use a consistent template for every finding.

**Example Finding Template:**
- **ID**: VULN-01
- **Name**: SQL Injection in Login Page
- **Severity**: Critical
- **Status**: Open
- **Description**: The `/login.php` page is vulnerable to Union-based SQLi.
- **PoC**: `admin' UNION SELECT 1,user(),database() --`
- **Impact**: Full database disclosure.
- **Fix**: Use prepared statements.

### 3. Automating Report Data
Some tools can export results directly into a report format:
- **Nmap**: `nmap -oX scan.xml <target>` (Export to XML for report tools).
- **Nessus**: Export as PDF or CSV.
- **Burp Suite**: Export as a project file for later review.
