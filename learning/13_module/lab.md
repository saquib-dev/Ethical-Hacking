# Module 13: Linux PrivEsc Lab

### Task 1: Sudo Enumeration
1. Log into a Linux VM as a low-privilege user.
2. Run `sudo -l`.
3. If you see a command you can run as root (e.g., `vim`), go to **GTFOBins**, search for that command, and follow the "Sudo" section to get a root shell.

### Task 2: SUID Hunting
1. Use the `find` command to list all SUID binaries on the system.
2. Identify a binary that is not a standard system tool.
3. Search for that binary on **GTFOBins** and attempt to escalate privileges.

### Task 3: Automated Enumeration
1. Download and run `LinPEAS` on the target system.
2. Look for the **RED/YELLOW** highlights (these are 95% likely to be privilege escalation vectors).
3. Use the information provided by LinPEAS to find a vulnerability and exploit it.

### Task 4: Kernel Exploitation
1. Check the kernel version using `uname -a`.
2. Search for that version on **Exploit-DB** or using `searchsploit`.
3. If a local exploit exists, compile it on the target and run it to get root.
