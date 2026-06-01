# Hashcat Commands Cheat Sheet

## Basic Syntax
```bash
hashcat -m [hash_type] -a [attack_mode] [hash_file] [dictionary_or_mask]
```

## Hash Types (`-m`)
- `-m 0` - MD5
- `-m 100` - SHA1
- `-m 1000` - NTLM
- `-m 1800` - SHA-512 (Unix)
- `-m 3200` - bcrypt
- `-m 13000` - RAR5
- `-m 13400` - KeePass
- *Use `hashcat -h | grep [keyword]` to find specific hash types.*

## Attack Modes (`-a`)
- `-a 0` - Straight (Dictionary attack)
- `-a 1` - Combination
- `-a 3` - Brute-force (Mask attack)
- `-a 6` - Hybrid Wordlist + Mask
- `-a 7` - Hybrid Mask + Wordlist

## Dictionary Attack Example
```bash
hashcat -m 1000 -a 0 hashes.txt rockyou.txt
```
*(Cracks NTLM hashes using the rockyou wordlist)*

## Mask Attack Example (Brute-force)
```bash
hashcat -m 0 -a 3 hashes.txt ?a?a?a?a?a
```
*(Cracks MD5 hashes brute-forcing all 5-character combinations)*

### Mask Charsets
- `?l` - Lowercase letters (a-z)
- `?u` - Uppercase letters (A-Z)
- `?d` - Digits (0-9)
- `?s` - Special characters
- `?a` - All of the above

## Rule-Based Attack Example
```bash
hashcat -m 0 -a 0 hashes.txt rockyou.txt -r /usr/share/hashcat/rules/best64.rule
```

## Useful Flags
- `--show` - Display cracked hashes.
- `-O` - Enable optimized kernels (limits password length but faster).
- `-w 3` - Workload profile (1=Low, 2=Default, 3=High, 4=Nightmare).
