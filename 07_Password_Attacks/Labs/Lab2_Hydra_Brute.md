# Lab 2: Online Brute Force with Hydra

## Goal: Guess a password for a service.

## WARNING: Only use this on your own VM!

## Steps:
1. **Target**: Your own Kali machine or a vulnerable VM.
2. **Command**:
   `hydra -l admin -P /usr/share/wordlists/rockyou.txt <target_ip> ssh`
   - `-l`: Username
   - `-P`: Path to password list
   - `ssh`: The service being attacked.

## Success Check:
- [ ] Found the correct password.
- [ ] Understand why online attacks are slower and noisier than offline ones.
