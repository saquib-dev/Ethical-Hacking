# Gobuster Commands Cheat Sheet

## Directory/File Brute-Forcing (`dir` mode)
```bash
# Basic directory brute-forcing
gobuster dir -u http://example.com -w /usr/share/wordlists/dirb/common.txt

# Search for specific file extensions
gobuster dir -u http://example.com -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt

# Ignore specific status codes (e.g., 404, 403)
gobuster dir -u http://example.com -w wordlist.txt -b 403,404

# Specify a custom User-Agent
gobuster dir -u http://example.com -w wordlist.txt -a "Mozilla/5.0 Windows NT 10.0"

# Set a cookie for authenticated scans
gobuster dir -u http://example.com -w wordlist.txt -c "session_id=12345"
```

## DNS Subdomain Brute-Forcing (`dns` mode)
```bash
# Basic subdomain brute-forcing
gobuster dns -d example.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-110000.txt

# Show CNAME records
gobuster dns -d example.com -w wordlist.txt -c

# Show IP addresses
gobuster dns -d example.com -w wordlist.txt -i
```

## Virtual Host Brute-Forcing (`vhost` mode)
```bash
# Basic vhost brute-forcing
gobuster vhost -u http://example.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-110000.txt

# Append domain to wordlist items
gobuster vhost -u http://example.com -w wordlist.txt --append-domain
```

## General Options
```bash
# Specify output file
gobuster dir -u http://example.com -w wordlist.txt -o results.txt

# Number of concurrent threads (default 10)
gobuster dir -u http://example.com -w wordlist.txt -t 50
```
