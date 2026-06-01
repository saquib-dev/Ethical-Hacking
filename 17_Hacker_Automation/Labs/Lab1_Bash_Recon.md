# Lab 1: Automating Recon with Bash

## Goal: Create a script that automates the first 3 steps of recon.

## Task:
Write a bash script `recon.sh` that does the following:
1. Takes a domain as an argument.
2. Runs `whois` on the domain.
3. Runs `nmap -sV` on the domain.
4. Saves all output into a folder named after the domain.

## Example Structure:
```bash
#!/bin/bash
DOMAIN=$1
mkdir $DOMAIN
whois $DOMAIN > $DOMAIN/whois.txt
nmap -sV $DOMAIN > $DOMAIN/nmap.txt
```

## Success Check:
- [ ] Script runs without errors.
- [ ] All results are neatly organized in folders.
