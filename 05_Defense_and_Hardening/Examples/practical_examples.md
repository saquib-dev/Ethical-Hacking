# Module 05: Practical Examples in Service Enumeration

## 1. Web Directory Brute-Forcing (Port 80/443)

You found a web server running on the target. If you visit the homepage, it's just a blank page. How do you find hidden content? You use a directory brute-forcer like `Gobuster` or `ffuf`.

**Command:**
```bash
# -u : The target URL
# -w : The wordlist of common directory names
$ gobuster dir -u http://10.10.10.20 -w /usr/share/wordlists/dirb/common.txt
```

**Output:**
```text
/assets               (Status: 301) [Size: 315] [--> http://10.10.10.20/assets/]
/images               (Status: 301) [Size: 315] [--> http://10.10.10.20/images/]
/index.html           (Status: 200) [Size: 114]
/secret_backup.zip    (Status: 200) [Size: 4092]
/admin_login.php      (Status: 200) [Size: 854]
```
*Takeaway:* The enumeration tool found a hidden backup file (`secret_backup.zip`) and a hidden login page (`/admin_login.php`) that were not linked anywhere on the main page. This gives you direct vectors to attack.

## 2. SMB Share Enumeration (Port 445)

Server Message Block (SMB) is used to share files. Often, network administrators accidentally leave shares open to "Null Sessions" (meaning anyone can log in without a password).

**Command:**
```bash
# -L : List shares
# -U "" : Use an empty (Null) username
# -N : No password
$ smbclient -L //10.10.10.20 -U "" -N
```

**Output:**
```text
    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    IPC$            IPC       IPC Service
    HR_Documents    Disk      Human Resources Public Share
    IT_Backups      Disk      IT Dept Backup Folder
```
*Takeaway:* You found custom file shares (`HR_Documents` and `IT_Backups`). Your next step is to connect directly to `//10.10.10.20/IT_Backups` and download all the files to search for hardcoded passwords or configuration data.
