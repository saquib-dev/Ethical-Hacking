# Module 02: Linux Mastery Lab

### Task 1: File System Scavenger Hunt
1. Navigate to `/etc`.
2. Find a file that contains the word "network" using `grep`.
3. Find the first 10 lines of the `/etc/passwd` file.
4. List all files in `/bin` that start with the letter "z".

### Task 2: The Permission Challenge
1. Create a directory named `secret_vault`.
2. Inside it, create a file named `password.txt` containing "SuperSecret123".
3. Change the permissions of `password.txt` to `600` (Only owner can read/write).
4. Try to read the file as a normal user. Then, use `sudo cat` to read it.
5. Change the owner of the file to a different user (if you have another account) or change the group.

### Task 3: Pipeline Practice
1. Use `ls /etc` and pipe the output into `grep` to find all files containing the word "conf".
2. Save that list of configuration files into a file named `configs.txt` in your home directory.
3. Count how many configuration files were found using the `wc -l` command:
   `cat configs.txt | wc -l`
