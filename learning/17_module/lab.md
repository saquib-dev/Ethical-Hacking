# Module 17: Active Directory I Lab

### Task 1: Domain Enumeration
1. Gain access to a machine joined to an AD domain.
2. Use `net user /domain` to list all users.
3. Use `net group "Domain Admins" /domain` to identify the administrators.
4. Use `nltest /domain_trusts` to see if there are other trusted domains.

### Task 2: AS-REP Roasting
1. Use `impacket-GetNPUsers` against the domain controller.
2. Identify users who do not require pre-authentication.
3. Save the hashes to a file.
4. Use `hashcat` with mode `-m 18200` and `rockyou.txt` to crack one of the passwords.

### Task 3: Kerberoasting
1. Use `impacket-GetUserSPNs` to find services with SPNs.
2. Request the service tickets and save the hashes.
3. Use `hashcat` with mode `-m 13100` to crack the service account password.
4. Use the cracked password to log into the service (e.g., via `impacket-psexec`).
