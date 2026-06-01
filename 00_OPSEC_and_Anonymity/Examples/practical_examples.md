# Module 00: Practical Examples in Ethical Hacking

## 1. Example Scope of Work (SOW) & Rules of Engagement (ROE)

Before any technical work begins, a professional ethical hacker needs explicit written permission. Here is a realistic example of how a Scope of Work is defined:

**Target Organization:** ACME Corp
**Testing Window:** October 15, 2023 – October 25, 2023, between 00:00 and 04:00 EST only.

**In-Scope:**
- `192.168.1.50` (Primary Web Server)
- `192.168.1.51` (Database Server)
- `*.acmecorp.com` (All subdomains)

**Out-of-Scope (DO NOT TOUCH):**
- `192.168.1.100` (Legacy HR System - fragile)
- Physical social engineering (e.g., tailgating into the building)

**Rules of Engagement:**
- No Denial of Service (DoS) or Distributed Denial of Service (DDoS) attacks.
- If Administrative/Root access is gained, the tester must take a screenshot as proof of access but must NOT alter or delete any data.

## 2. The 5 Phases: A Practical Scenario

Let's imagine you are hacking a target machine (`10.10.10.5`) in a lab environment.

1. **Reconnaissance:** You browse the target company's website and look at their LinkedIn pages. You find an IT admin's email address: `j.smith@acmecorp.com`.
2. **Scanning & Enumeration:** You run a tool against the target IP and find that port `22` (SSH) and port `80` (HTTP) are open. You discover the web server is running an outdated version of WordPress.
3. **Gaining Access (Exploitation):** You find a known vulnerability for that exact WordPress version. You use an exploit script to bypass the login page and upload a "web shell," giving you remote command execution.
4. **Maintaining Access:** To ensure you don't lose access if the server reboots, you add a new hidden user account (`backup_admin`) to the system with a password only you know.
5. **Covering Tracks/Reporting:** In a real malicious scenario, the hacker deletes the `/var/log/auth.log` file to hide their login. As an *ethical* hacker, you skip deleting logs and instead write a detailed report explaining to ACME Corp how to update WordPress and secure their server.
