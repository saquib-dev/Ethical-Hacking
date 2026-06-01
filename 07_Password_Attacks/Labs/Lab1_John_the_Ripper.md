# Lab 1: Offline Cracking with John the Ripper

## Goal: Crack a simple hash.

## Steps:
1. **Create a hash**:
   `echo "password123" | md5sum > hash.txt`
2. **Run John**:
   `john hash.txt`
3. **See the result**:
   `john --show hash.txt`

## Challenge:
Try using the `rockyou.txt` wordlist (found in `/usr/share/wordlists/rockyou.txt` on Kali).
`john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt`

## Success Check:
- [ ] Successfully cracked the hash.
- [ ] Understand the difference between a dictionary attack and brute force.
