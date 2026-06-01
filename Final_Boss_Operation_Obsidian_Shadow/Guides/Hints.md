# The Hacker's Guide (Hints)

*Do not read these unless you are completely stuck. A real hacker spends hours in the "darkness" before finding the light.*

## Hint 1: The Perimeter
If you can't find a way in, look at the "Contact Us" or "Upload Resume" features. Does the server validate the file type? If not, a web shell is your best friend.

## Hint 2: The Internal Pivot
Once you are in the web server, remember that you are now *inside* the firewall. Use `nmap` to find other machines. If you find an API, look for parameters like `?id=123`. What happens if you change the ID?

## Hint 3: The AD Forest
Once you have a user account, you are a "foot in the door." Use `GetUserSPNs.py` to see if any service accounts have weak passwords. If you get a hash, `hashcat` is the way.

## Hint 4: The Binary Secret
The binary on the DC is a simple "Password Checker." Don't try to guess the password. Open it in Ghidra, look at the `main` function, and look for strings that look like AWS keys (`AKIA...`).

## Hint 5: The Cloud Vault
Use the `aws s3 ls` command with the stolen keys. If you get an "Access Denied," check if you have the right role.
