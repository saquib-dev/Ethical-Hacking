# Lab: Directory Enumeration with Gobuster

## Scenario
You are performing a web application assessment on `http://target-ip/`. Your goal is to discover hidden directories and files that might contain sensitive information or administrative interfaces.

## Objectives
1. Use Gobuster to discover hidden directories.
2. Search for specific file types (e.g., `.php`, `.txt`).
3. Identify a hidden administrative page or backup file.

## Steps
1. **Basic Enumeration:** Run a standard directory scan using a common wordlist.
   ```bash
   gobuster dir -u http://target-ip -w /usr/share/wordlists/dirb/common.txt
   ```
2. **Review Results:** Note any interesting directories returning a 200 (OK) or 301 (Redirect) status code. For example, if you find an `/admin` directory.
3. **Targeted Scan:** Run a more extensive scan looking for specific file extensions.
   ```bash
   gobuster dir -u http://target-ip -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,txt,bak
   ```
4. **Investigate Findings:** If Gobuster finds a file like `config.php.bak` or `robots.txt`, access it via your browser or `curl` to view its contents.

## Conclusion
By utilizing Gobuster, you systematically uncovered hidden paths on the web server, demonstrating the importance of removing unnecessary files and restricting access to administrative areas.
