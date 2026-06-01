# John the Ripper Examples

## Scenario: Cracking Linux Password Hashes

You have successfully exploited a Linux server and extracted the `/etc/passwd` and `/etc/shadow` files. You want to crack the user passwords offline.

### Preparation

First, combine the files using the `unshadow` utility provided by John the Ripper suite.

```bash
unshadow passwd.txt shadow.txt > unshadowed.txt
```

### Command

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt unshadowed.txt
```

### Explanation of Flags
* `--wordlist=...`: Specifies the dictionary file to use for wordlist-based cracking.
* `unshadowed.txt`: The input file containing the combined user and hash information.

### Mocked Terminal Output

```text
Loaded 2 password hashes with 2 different salts (sha512crypt, crypt(3) $6$ [SHA512 256/256 AVX2 4x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
password123      (alice)
iloveyou         (bob)
2g 0:00:00:05 DONE (2024-05-31 11:05) 0.3584g/s 20456p/s 40912c/s 40912C/s 123456..jennifer
Use the "--show" option to display all of the cracked passwords reliably
Session completed
```
