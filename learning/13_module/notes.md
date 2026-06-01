# Module 13: Linux Privilege Escalation (PrivEsc)

## 1. What is Privilege Escalation?
Privilege escalation is the act of gaining a higher level of permission on a system than you were initially granted. Usually, this means moving from a low-privilege user (like `www-data`) to the root user (superuser).

## 2. The "Low-Hanging Fruit"
Before using complex exploits, always check for common misconfigurations.

### A. SUID Bit (Set User ID)
The SUID bit allows a file to be executed with the permissions of the file owner (often root) rather than the user running it.
- If a binary like `find` or `vim` has the SUID bit set, you can use it to escape to a root shell.
- **Check for SUID files**: `find / -perm -4000 2>/dev/null`

### B. Sudo Misconfigurations
Some users are allowed to run specific commands as root without a password.
- **Check your sudo permissions**: `sudo -l`
- If you can run `/usr/bin/perl` as sudo, you can execute any command as root.

### C. Writable `/etc/passwd`
In older systems, if `/etc/passwd` is writable, you can add a new root user with a known password.

### D. Cron Jobs
Cron jobs are scheduled tasks. If a root-level cron job runs a script that you can edit, you can add a reverse shell to that script and wait for it to execute.

## 3. Kernel Exploits
If the OS kernel is outdated, you can use a "Local Privilege Escalation" (LPE) exploit.
- **Example**: Dirty COW (CVE-2016-5195).
- **Caution**: Kernel exploits are risky and can crash the entire system. Always check the kernel version first.
