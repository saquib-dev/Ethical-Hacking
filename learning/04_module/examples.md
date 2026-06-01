# Module 04: Practical Examples in Network Scanning

## 1. A Real-World Nmap Scan Example

Let's look at how an ethical hacker uses Nmap to discover open doors on a target machine.

### The Stealth Scan (TCP SYN)
A common scan is the "Stealth" scan (`-sS`). It is fast and attempts to avoid logging by tearing down the connection right before it is fully established. 

```bash
# -sS : SYN Scan (Stealth)
# -sV : Version detection (probe open ports to determine service/version info)
# -p- : Scan all 65,535 ports (instead of just the top 1000)
# 10.10.10.20 : The target IP
$ sudo nmap -sS -sV -p- 10.10.10.20
```

### Example Nmap Output
```text
Starting Nmap 7.93 ( https://nmap.org ) at 2023-10-15 14:00 EDT
Nmap scan report for 10.10.10.20
Host is up (0.045s latency).
Not shown: 65532 closed tcp ports (reset)

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
445/tcp open  smb    Samba smbd 4.6.2

Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

## 2. Analyzing the Scan Results

As a hacker, looking at the output above gives you immediate attack paths:
1. **Port 22 (SSH):** It's running OpenSSH 8.2p1. You might try to brute-force usernames and passwords here later, but SSH is usually secure against exploit scripts unless a critical CVE exists.
2. **Port 80 (HTTP):** An Apache 2.4.41 web server is running. Your next step would be to open your web browser, navigate to `http://10.10.10.20`, and see what the website looks like.
3. **Port 445 (SMB):** File sharing is enabled. You immediately know you need to try and list the file shares to see if there are any documents left completely public or accessible without a password.
