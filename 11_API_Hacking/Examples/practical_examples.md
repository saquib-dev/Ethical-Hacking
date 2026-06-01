# Module 11 Examples: Password Cracking & Hash Analysis

## 1. Identifying the Hash Type
Before cracking, you must know what algorithm was used. Tools like `hashid` or `name-that-hash` can help.
```bash
$ hashid 5d41402abc4b2a76b9719d911017c592
Analyzing '5d41402abc4b2a76b9719d911017c592'
[+] MD5 
[+] MD4 
```

## 2. Cracking with Hashcat
Hashcat is highly optimized for GPU cracking.
- `-m 0` defines the hash type (0 = MD5).
- `-a 0` defines the attack mode (0 = Dictionary attack).

```bash
# Dictionary attack using rockyou.txt
hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt

# Expected Output snippet:
# 5d41402abc4b2a76b9719d911017c592:hello
# Status...........: Cracked
```

## 3. Cracking with John the Ripper (JTR)
JTR is excellent for CPU cracking and handles many formats automatically (like Linux `/etc/shadow` hashes).

**Step 1: Unshadowing (Linux)**
Combine the `passwd` and `shadow` files so John can read them properly.
```bash
unshadow /tmp/passwd /tmp/shadow > unshadowed_hashes.txt
```

**Step 2: Cracking**
```bash
john --wordlist=/usr/share/wordlists/rockyou.txt unshadowed_hashes.txt

# Expected Output snippet:
# Loaded 2 password hashes...
# Password123      (root)
```
