# Module 11: Cracking Command Reference

### 1. John the Ripper (JtR)
Great for simple files and automatic hash detection.

| Command | Description | Use Case |
| :--- | :--- | :--- |
| `john <hash_file>` | Auto-detect and crack | Quick start. |
| `john --wordlist=<list> <hash_file>` | Dictionary attack | Using `rockyou.txt`. |
| `john --show <hash_file>` | Show cracked passwords | View results. |

### 2. Hashcat
The fastest cracker in the world. It uses the **GPU** instead of the CPU.

**The Hashcat Formula:** `hashcat -m <type> -a <attack> <hash> <wordlist>`

| Component | Common Values | Meaning |
| :--- | :--- | :--- |
| **-m (Type)** | `0` (MD5), `100` (SHA1), `1800` (SHA512) | The algorithm. |
| **-a (Attack)** | `0` (Straight/Dict), `3` (Brute-force) | The method. |

**Examples:**
- **MD5 Dictionary Attack**:
  `hashcat -m 0 -a 0 hash.txt /usr/share/wordlists/rockyou.txt`
- **SHA-1 Brute Force (6 characters)**:
  `hashcat -m 100 -a 3 hash.txt ?a?a?a?a?a?a`

### 3. Useful Utilities
- **Hash-ID**: `hash-id <hash>` (Tells you what algorithm was used).
- **Rockyou.txt**: The legendary wordlist located at `/usr/share/wordlists/rockyou.txt.gz`.
  - *To unzip it*: `sudo gunzip /usr/share/wordlists/rockyou.txt.gz`

### The "Cracking Chain" (Example):
Steal hash $\rightarrow$ Identify hash type $\rightarrow$ Choose wordlist $\rightarrow$ Crack:
```bash
hash-id "5d41402abc4b2a76b971//..." && hashcat -m 0 -a 0 hash.txt rockyou.txt
```
