# Module 02: Practical Examples in the Linux CLI

## 1. Navigating and Understanding Permissions

Imagine you have just compromised a low-privilege user account on a Linux server and are trying to read a sensitive file.

```bash
# You check who you are logged in as
$ whoami
john

# You list the files in the current directory with their permissions
$ ls -l
-rw-r--r-- 1 root root  1045 Oct 15 10:00 public_notes.txt
-rwx------ 1 root root  2048 Oct 15 10:05 secret_script.sh
```

**Breaking down `-rwx------ 1 root root`:**
- The first `-` means it's a file.
- `rwx` means the **owner** (which is `root`) can Read, Write, and eXecute the script.
- `---` means the **group** has no permissions.
- `---` means **others** (like our user `john`) have no permissions.

If user `john` tries to run or read it:
```bash
$ ./secret_script.sh
bash: ./secret_script.sh: Permission denied
```

## 2. Chaining Commands with Pipes (`|`) and Redirection (`>`)

Pipes are incredibly powerful for parsing large amounts of data, which is essential during enumeration.

**Example 1: Finding Active Users**
You want to see all users on the system who have a valid shell (meaning they can log in), and save that list to a file for later brute-forcing.

```bash
# cat reads the file
# grep filters out only lines containing "/bin/bash"
# > redirects the output into a new file named valid_users.txt
$ cat /etc/passwd | grep "/bin/bash" > valid_users.txt
```

**Example 2: Discovering Hidden Files**
You want to find all files on the entire hard drive that belong to the user `root` and have the "SUID" bit set (a common way to escalate privileges to root).

```bash
# find starts searching from the root directory (/)
# -user root looks for files owned by root
# -perm -4000 looks for the SUID permission
# 2>/dev/null takes all the "Permission denied" errors and throws them in the trash, leaving only clean results
$ find / -type f -user root -perm -4000 2>/dev/null
```
