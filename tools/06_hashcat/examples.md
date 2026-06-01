# Hashcat Examples

## Scenario: Cracking NTLM Hashes

During a Windows domain compromise, you dumped the NTDS.dit and extracted the NTLM hashes. You want to crack a specific administrator's hash using a dictionary attack combined with rules.

The file `hashes.txt` contains: `aad3b435b51404eeaad3b435b51404ee:8846f7eaee8fb117ad06bdd830b7586c`

### Command

```bash
hashcat -m 1000 -a 0 hashes.txt /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule
```

### Explanation of Flags
* `-m 1000`: Sets the hash type to NTLM.
* `-a 0`: Sets the attack mode to Straight (dictionary attack).
* `hashes.txt`: The input file containing the hashes.
* `/usr/share/wordlists/rockyou.txt`: The wordlist to use.
* `-r ...`: Applies mutation rules to the wordlist (e.g., appending numbers, capitalizing first letter).

### Mocked Terminal Output

```text
hashcat (v6.2.6) starting

OpenCL API (OpenCL 3.0 CUDA 12.1.109) - Platform #1 [NVIDIA Corporation]
========================================================================
* Device #1: NVIDIA GeForce RTX 3080, 8192/10240 MB (2560 MB allocatable), 68MCU

Minimum password length supported by kernel: 0
Maximum password length supported by kernel: 256

Hashes: 1 digests; 1 unique digests, 1 unique salts
Bitmaps: 16 bits, 65536 entries, 0x0000ffff mask, 262144 bytes, 5/13 rotates
Rules: 64

Dictionary cache hit:
* Filename..: /usr/share/wordlists/rockyou.txt
* Passwords.: 14344384
* Bytes.....: 139921497
* Keyspace..: 918040576

8846f7eaee8fb117ad06bdd830b7586c:Winter2023!

Session..........: hashcat
Status...........: Cracked
Hash.Mode........: 1000 (NTLM)
Hash.Target......: 8846f7eaee8fb117ad06bdd830b7586c
Time.Started.....: Fri May 31 11:30:00 2024 (2 secs)
Time.Estimated...: Fri May 31 11:30:02 2024 (0 secs)
Speed.Dev.#1.....: 512.4 MH/s (2.36ms) @ Accel:256 Loops:1 Thr:256 Vec:1
Recovered........: 1/1 (100.00%) Digests (total), 1/1 (100.00%) Digests (new)
```
