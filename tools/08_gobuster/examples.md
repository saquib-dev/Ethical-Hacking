# Gobuster Examples

## Scenario: Directory and File Enumeration

You are assessing a web server at `http://192.168.1.100` and want to discover hidden directories and files (specifically `.php` and `.txt` files) using a wordlist.

### Command

```bash
gobuster dir -u http://192.168.1.100 -w /usr/share/wordlists/dirb/common.txt -x php,txt -t 20
```

### Explanation of Flags
* `dir`: Specifies directory enumeration mode.
* `-u ...`: The target URL.
* `-w ...`: The path to the wordlist.
* `-x php,txt`: Extensions to append to each wordlist item (checks for file.php, file.txt, etc.).
* `-t 20`: Number of concurrent threads to use (speeds up the process).

### Mocked Terminal Output

```text
===============================================================
Gobuster v3.5
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://192.168.1.100
[+] Method:                  GET
[+] Threads:                 20
[+] Wordlist:                /usr/share/wordlists/dirb/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.5
[+] Extensions:              php,txt
[+] Timeout:                 10s
===============================================================
2024/05/31 12:00:00 Starting gobuster in directory enumeration mode
===============================================================
/.hta                 (Status: 403) [Size: 278]
/.htaccess            (Status: 403) [Size: 278]
/.htpasswd            (Status: 403) [Size: 278]
/admin                (Status: 301) [Size: 316] [--> http://192.168.1.100/admin/]
/config.php           (Status: 200) [Size: 0]
/css                  (Status: 301) [Size: 314] [--> http://192.168.1.100/css/]
/images               (Status: 301) [Size: 317] [--> http://192.168.1.100/images/]
/index.php            (Status: 200) [Size: 1450]
/login.php            (Status: 200) [Size: 980]
/robots.txt           (Status: 200) [Size: 42]
/server-status        (Status: 403) [Size: 278]
/uploads              (Status: 301) [Size: 318] [--> http://192.168.1.100/uploads/]
===============================================================
2024/05/31 12:00:15 Finished
===============================================================
```
