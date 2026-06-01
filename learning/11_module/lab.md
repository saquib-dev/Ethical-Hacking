# Module 11: Password Cracking Lab

### Task 1: Identify the Hash
1. Copy these three hashes:
   - `5d41402abc4b2a76b971//`
   - `7c4a8d09ca3762af61e59520943dc264`
   - `$6$rounds=5000$saltsalt$hashedpassword...`
2. Use `hash-id` to determine which algorithm was used for each.

### Task 2: Cracking with John the Ripper
1. Create a file `hashes.txt` and put a few MD5 hashes in it (you can generate some online).
2. Run `john hashes.txt`.
3. Use `john --show hashes.txt` to see the decrypted passwords.

### Task 3: High-Performance Cracking with Hashcat
1. Unzip the rockyou wordlist: `sudo gunzip /usr/share/wordlists/rockyou.txt.gz`.
2. Take an MD5 hash of the word "password" (use an online generator).
3. Save it to `target.txt`.
4. Run `hashcat -m 0 -a 0 target.txt /usr/share/wordlists/rockyou.txt`.
5. Observe how much faster Hashcat is than JtR.

### Task 4: Brute Forcing
1. Create a hash of a 4-character password (e.g., "1234").
2. Use Hashcat with a mask to crack it:
   `hashcat -m 0 -a 3 target.txt ?d?d?d?d`
   (`?d` stands for digits 0-9).
