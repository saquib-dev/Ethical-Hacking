# Module 11: Password Cracking & Hash Analysis

## 1. Hashing vs. Encryption
The most common mistake for beginners is confusing these two.

| Feature | Encryption | Hashing |
| :--- | :--- | :--- |
| **Type** | Two-way (Reversible) | One-way (Irreversible) |
| **Purpose** | Confidentiality (Secret msg) | Integrity (Password storage) |
| **Key** | Requires a key to decrypt | No key; same input always $\rightarrow$ same hash |
| **Example** | AES, RSA | MD5, SHA-256, bcrypt |

## 2. How Password Cracking Works
Since hashes are irreversible, we can't "decrypt" them. Instead, we use **Hash Comparison**:
1. Take a known password (e.g., `password123`).
2. Hash it using the same algorithm (e.g., MD5).
3. Compare the result with the stolen hash. If they match, you found the password.

### Cracking Methods
- **Dictionary Attack**: Using a list of common passwords (e.g., `rockyou.txt`).
- **Brute Force**: Trying every possible combination of characters (Very slow).
- **Rainbow Tables**: Pre-computed tables of hashes for millions of passwords.

## 3. Salting: The Defense
To stop Rainbow Tables, developers use a **Salt**. A salt is a random string added to the password before hashing.
- **Without Salt**: `password123` $\rightarrow$ `hash_A` (Same for everyone).
- **With Salt**: `password123 + "xyz789"` $\rightarrow$ `hash_B` (Unique for everyone).

## 4. Common Hash Types
- **MD5**: Fast, very insecure (Collisions).
- **SHA-1**: Common, now considered weak.
- **bcrypt/scrypt**: Slow (computationally expensive), very secure. Used for modern passwords.
