# Module 15: Post-Exploitation Lab

### Task 1: Establishing Persistence
1. Gain a shell on a Linux VM.
2. Create a simple bash script `/tmp/shell.sh` that executes a reverse shell.
3. Add a cron job to run that script every minute.
4. Kill your current shell.
5. Wait 60 seconds and observe your listener; you should get a new shell automatically.

### Task 2: Windows Registry Persistence
1. Gain a shell on a Windows VM.
2. Use the `reg add` command in `commands.md` to add your payload to the "Run" key.
3. Reboot the VM.
4. Verify that your reverse shell connects back to you immediately after login.

### Task 3: Pivoting Practice
1. Set up two VMs: **Victim A** (exposed to Kali) and **Victim B** (only exposed to Victim A).
2. Compromise Victim A.
3. Use Meterpreter's `route add` or **Chisel** to create a tunnel to Victim B's network.
4. Use `proxychains` to run an Nmap scan on Victim B from your Kali machine.

### Task 4: Stealth Mode
1. Use the `touch` command to change the date of your malicious file to match a system file:
   `touch -r /bin/ls /tmp/shell.sh`
2. Clear the event logs on the Windows machine using `wevtutil`.
