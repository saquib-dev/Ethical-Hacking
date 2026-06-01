# Module 05: Enumeration Lab

### Task 1: Web Directory Brute-forcing
1. Launch a target (e.g., a VM from TryHackMe or an intentionally vulnerable site).
2. Use `gobuster` with the `common.txt` wordlist to find hidden directories.
3. Visit any directory found (e.g., `/backup`) in your browser and see if there are files available.
4. Run `nikto` on the target and identify one "interesting" finding.

### Task 2: SMB Reconnaissance
1. Use `enum4linux -a <target>` against a Windows-based target.
2. Identify:
   - The OS version.
   - A list of shared folders.
   - A list of local users.
3. Use `smbclient -L \\\\<target>\\` to confirm the shares.

### Task 3: DNS Intelligence
1. Use `whois` on a domain you own or a public domain to find registration details.
2. Use `dig` to find the Mail Exchange (MX) records for a target domain.
3. Try a Zone Transfer (`axfr`) against a known misconfigured DNS server (if available in your lab).
