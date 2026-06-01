# sqlmap Notes

## Overview
sqlmap is an open-source penetration testing tool that automates the process of detecting and exploiting SQL injection flaws and taking over database servers.

## How It Works
sqlmap sends a variety of crafted SQL queries to the target application and analyzes the responses. It uses different techniques to identify vulnerabilities:
- **Boolean-based blind:** Inferring data by asking TRUE/FALSE questions.
- **Time-based blind:** Inferring data based on the time the database takes to respond.
- **Error-based:** Extracting data from database error messages.
- **UNION query-based:** Combining the results of the original query with the injected query.
- **Stacked queries:** Executing multiple SQL statements sequentially.

## Best Practices & Considerations
- **Authorization:** ONLY use sqlmap on systems you have explicit permission to test.
- **Rate Limiting:** Automated tools can be loud. Use options like `--delay` to slow down requests and evade basic detection mechanisms.
- **WAF/IPS:** Web Application Firewalls may block sqlmap payloads. Use `--tamper` scripts to obfuscate payloads.
- **Risk of Data Loss:** Exploit options like `--os-shell` or `--sql-shell` can modify or damage the database if not used carefully.
- **Session Handling:** When testing authenticated pages, ensure you provide the correct session cookies (`--cookie`) or use a request file (`-r`).
