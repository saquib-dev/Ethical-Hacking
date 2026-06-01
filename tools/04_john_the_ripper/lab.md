# John the Ripper Practice Lab

## Scenario
You have obtained a password dump containing Linux `/etc/shadow` style hashes. Your objective is to extract the plaintext passwords using John the Ripper.

## Objectives
1. Identify the hash type.
2. Prepare the environment and necessary wordlists.
3. Crack the hashes using a dictionary attack.
4. View the cracked passwords.

## Steps

### Step 1: Preparation
1. Create a file named `hashes.txt` containing the target hashes.
2. Ensure you have the `rockyou.txt` wordlist available. (Usually located at `/usr/share/wordlists/rockyou.txt` on Kali Linux).

### Step 2: Unshadowing (If applicable)
If you have both `passwd` and `shadow` files, combine them:
```bash
unshadow passwd.txt shadow.txt > unshadowed_hashes.txt
```

### Step 3: Cracking the Hashes
Run a wordlist attack against the hash file:
```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
```

### Step 4: Verification
Once John finishes, view the cracked passwords:
```bash
john --show hashes.txt
```

## Challenge
Try to crack a ZIP file protected with a password.
1. Create a password-protected zip.
2. Use `zip2john` to extract the hash.
3. Crack the hash with John the Ripper.
