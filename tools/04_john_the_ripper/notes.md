# John the Ripper Overview

## What is John the Ripper?
John the Ripper (JtR) is a fast, versatile password cracker. Its primary purpose is to detect weak Unix passwords, but it supports hundreds of hash and cipher types, including Windows LM/NTLM hashes, macOS hashes, database hashes, and document encryption (PDF, ZIP, RAR).

## How it Works
John the Ripper operates by taking a list of potential passwords (either generated on the fly or read from a wordlist), hashing them using the same algorithm as the target hash, and comparing the results. If the hashes match, the password is recovered.

## Modes of Operation
1. **Single Crack Mode:** Uses username and GECOS information from the password file as candidate passwords. Very fast and highly effective for finding trivial passwords.
2. **Wordlist Mode:** Reads candidate passwords from a text file (dictionary).
3. **Wordlist + Rules Mode:** Takes a wordlist and applies mutation rules (e.g., adding numbers to the end, capitalizing the first letter) to increase the coverage.
4. **Incremental Mode:** A brute-force attack that tries every possible combination of characters up to a certain length.

## Best Practices
- **Start Simple:** Always start with Single Crack Mode, followed by a Wordlist attack (e.g., `rockyou.txt`), before resorting to time-consuming incremental brute-force attacks.
- **Identify Format:** Whenever possible, specify the hash format using `--format=` to save time, rather than relying on JtR's auto-detection.
- **Use Rules:** Wordlists combined with rules (like the 'KoreLogic' rules) are incredibly effective and much faster than pure brute-force.
- **Manage Sessions:** JtR automatically saves its progress in a session file (`john.rec`). You can pause an attack with `Ctrl+C` and resume it later using `john --restore`.
