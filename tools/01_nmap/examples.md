# Nmap Examples

## Scenario: Network Discovery and Vulnerability Scanning

You are conducting an internal penetration test and have been given a subnet to assess: `192.168.1.0/24`. Your goal is to identify active hosts, open ports, running services, and potential vulnerabilities.

### Command

```bash
nmap -p- -sV -sC -A -T4 -oN nmap_scan.txt 192.168.1.10
```

### Explanation of Flags
* `-p-`: Scans all 65535 ports.
* `-sV`: Probes open ports to determine service and version info.
* `-sC`: Runs default Nmap scripts (equivalent to `--script=default`).
* `-A`: Enables OS detection, version detection, script scanning, and traceroute.
* `-T4`: Sets timing template for faster execution.
* `-oN nmap_scan.txt`: Outputs the results in normal format to `nmap_scan.txt`.

### Mocked Terminal Output

```text
Starting Nmap 7.93 ( https://nmap.org ) at 2024-05-31 10:00 EDT
Nmap scan report for target.local (192.168.1.10)
Host is up (0.0010s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 9c:8a:3f:52:6c:e9:2e:cc:11:4a:d6:e4:65:42:07:95 (RSA)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Welcome to Our Vulnerable App!
MAC Address: 00:0C:29:A1:B2:C3 (VMware)
Device type: general purpose
Running: Linux 4.X|5.X
OS CPE: cpe:/o:linux:linux_kernel:5.4
OS details: Linux 4.15 - 5.6

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 15.34 seconds
```
