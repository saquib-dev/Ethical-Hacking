# Hashcat Practice Lab

## Scenario
During a penetration test, you dumped the local SAM database of a Windows machine and obtained NTLM hashes. You need to crack these hashes efficiently using GPU acceleration with Hashcat.

## Objectives
1. Identify the correct Hashcat module for NTLM hashes.
2. Perform a dictionary attack combined with mutation rules.
3. View the cracked results.

## Steps

### Step 1: Preparation
1. Save the dumped NTLM hashes into a file named `ntlm_hashes.txt`.
   Format example: `aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0`
2. Ensure you have the `rockyou.txt` wordlist.

### Step 2: Rule-Based Dictionary Attack
Run Hashcat using attack mode 0 (Straight), module 1000 (NTLM), the `rockyou.txt` wordlist, and the `best64.rule` rule set to mutate the words:
```bash
hashcat -m 1000 -a 0 ntlm_hashes.txt /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule -O -w 3
```
*(Note: `-O` optimizes the kernel, `-w 3` increases GPU workload for faster cracking).*

### Step 3: View Results
Once the session is complete (or aborted/paused), view the successfully cracked hashes:
```bash
hashcat -m 1000 --show ntlm_hashes.txt
```

## Challenge
Perform a mask attack to find a 4-digit PIN (MD5 hash).
1. Create an MD5 hash of a 4-digit number.
2. Use attack mode 3 and the mask `?d?d?d?d` to crack it.
