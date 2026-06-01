# Module 02: Mastering the Linux CLI

## 1. The Philosophy of Linux
In Linux, **everything is a file**. Your hard drive is a file, your keyboard is a file, and your system settings are files. If you can read and write files, you can control the system.

## 2. The File System Hierarchy (FHS)
Understanding where things are is half the battle.
*   `/root`: The home directory for the "God" user (root).
*   `/home`: Where regular users store their documents.
*   `/etc`: The "Control Panel" of Linux. Contains configuration files (e.g., `/etc/passwd`).
*   `/bin` & `/sbin`: Where the actual program files (binaries) live.
*   `/var/log`: Where the system records everything that happens. **Crucial for covering tracks.**
*   `/tmp`: Temporary files. Often the only place an attacker has permission to write files.

## 3. Permissions & Ownership
Linux uses a strict permission system to prevent users from breaking the system.

### The Permission String (`-rwxr-xr--`)
- First character: `-` (file) or `d` (directory).
- Next 3 (`rwx`): **Owner** permissions.
- Next 3 (`r-x`): **Group** permissions.
- Last 3 (`r--`): **Others** (everyone else).

### The Power of Sudo
`sudo` (SuperUser DO) allows a permitted user to execute a command as the root user. In hacking, you often start as a low-privilege user and try to "Escalate Privileges" to become root.

## 4. The Power of Pipes and Redirection
Linux allows you to chain commands together.
- **Pipe (`|`)**: Takes the output of command A and feeds it as input to command B.
- **Redirect (`>`)**: Overwrites a file with the output.
- **Append (`>>`)**: Adds output to the end of a file.
