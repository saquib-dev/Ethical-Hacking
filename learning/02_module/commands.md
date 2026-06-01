# Module 02: Essential Linux Commands

### 1. Navigation & Exploration
| Command | Description | Pro Tip |
| :--- | :--- | :--- |
| `pwd` | Print Working Directory | Know exactly where you are. |
| `ls -la` | List all files (including hidden) | `-a` shows hidden files (starting with `.`). |
| `cd ..` | Go up one directory | `cd ~` takes you home instantly. |
| `mkdir -p a/b/c` | Create nested directories | `-p` creates parents if they don't exist. |

### 2. File Manipulation
| Command | Description | Example |
| :--- | :--- | :--- |
| `cat <file>` | Display file content | `cat /etc/passwd` |
| `grep "text" <file>` | Search for a string | `grep "root" /etc/passwd` |
| `head -n 5 <file>` | View first 5 lines | Great for checking file headers. |
| `tail -n 5 <file>` | View last 5 lines | Great for watching logs in real-time. |
| `nano <file>` | Simple text editor | Use `Ctrl+O` to save, `Ctrl+X` to exit. |

### 3. System & Permissions
| Command | Description | Example |
| :--- | :--- | :--- |
| `chmod +x <file>` | Make file executable | Required for running custom scripts. |
| `chmod 600 <file>` | Read/Write for owner only | Used to protect SSH keys. |
| `chown user:group <file>` | Change owner | Used after gaining root to hide files. |
| `sudo su` | Become root | Use with caution; one mistake can kill the OS. |

### 4. The "Hacker's Chain" (Example)
Find all users on the system and save them to a file:
```bash
cat /etc/passwd | cut -d: -f1 > users.txt
```
*Explanation: Read passwd -> Split by colon -> Take first column -> Save to file.*
