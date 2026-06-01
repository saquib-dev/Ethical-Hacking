# Module 15: Post-Exploitation (Persistence & Pivoting)

## 1. What is Post-Exploitation?
Post-exploitation is what happens **after** you have successfully gained access to a system. The goal is to ensure you don't lose access and to use the compromised machine as a jumping-off point to attack other machines.

## 2. Persistence: Staying Inside
If the victim reboots their computer or changes their password, you lose your shell. Persistence ensures you can get back in.

### Common Persistence Methods:
- **Scheduled Tasks (Windows)**: Create a task that runs your reverse shell every hour.
- **Cron Jobs (Linux)**: Add a line to `/etc/crontab` to execute your shell daily.
- **Registry Run Keys (Windows)**: Add your payload to `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run`.
- **SSH Keys**: Add your public key to `/home/user/.ssh/authorized_keys` for permanent passwordless access.

## 3. Pivoting: Moving Through the Network
Most companies have a "DMZ" (where the web server is) and an "Internal Network" (where the database and domain controllers are). Your initial shell is usually in the DMZ. Pivoting allows you to "hop" from the DMZ to the internal network.

### Pivoting Techniques:
- **SSH Tunneling**: Forwarding traffic from your Kali machine through the compromised host to an internal target.
- **SOCKS Proxy**: Using a tool (like Chisel or Meterpreter) to turn the compromised host into a proxy server.
- **Port Forwarding**: Mapping a port on the victim machine to a port on another internal machine.

## 4. Clearing Tracks
To avoid detection by Blue Teams (Defenders) and EDR (Endpoint Detection and Response) tools:
- **Log Deletion**: Clear `/var/log/auth.log` or Windows Event Logs.
- **Timestomping**: Changing the "Modified Date" of your malicious files to match legitimate system files.
- **Removing Tools**: Delete your scripts and binaries before exiting.
