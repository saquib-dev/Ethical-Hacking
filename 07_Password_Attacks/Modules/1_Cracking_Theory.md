# Module 1: Password Cracking Theory

## What is Hashing?
Passwords aren't stored as plain text. They are turned into a "Hash" (a unique string of characters).
Example: `password123` $\rightarrow$ `ef92b778...`
Hashing is one-way; you cannot "un-hash" it.

## How Cracking Works:
1. **Dictionary Attack**: The tool tries a list of common passwords (like `rockyou.txt`) and hashes them to see if they match the target hash.
2. **Brute Force**: The tool tries every single possible combination of characters. (Very slow).
3. **Rainbow Tables**: Pre-computed tables of hashes for common passwords.

## Password Salts
A "Salt" is random data added to a password before hashing. This makes Rainbow Tables useless.
