# John the Ripper Commands Cheat Sheet

## Basic Cracking
- `john hash.txt` - Crack a simple hash file using default settings.
- `john --show hash.txt` - Show the cracked passwords.

## Wordlist Attack
- `john --wordlist=/path/to/wordlist.txt hash.txt` - Crack using a specific wordlist (e.g., rockyou.txt).
- `john --wordlist=rockyou.txt --rules hash.txt` - Use a wordlist with rules (mutations).

## Format Specification
- `john --format=nt hash.txt` - Specify the hash format (e.g., NT, raw-MD5, bcrypt).
- `john --list=formats` - List all supported hash formats.

## Single Crack Mode
- `john --single hash.txt` - Use single crack mode (uses login/GECOS information as passwords).

## Incremental/Brute-force
- `john --incremental hash.txt` - Brute-force mode (tries all character combinations).
- `john --incremental=Alpha hash.txt` - Brute-force using only alphabetical characters.

## SSH, ZIP, PDF Cracking
- `ssh2john id_rsa > ssh_hash.txt` - Convert SSH private key to JtR format.
- `zip2john file.zip > zip_hash.txt` - Convert ZIP archive to JtR format.
- `pdf2john file.pdf > pdf_hash.txt` - Convert PDF to JtR format.
