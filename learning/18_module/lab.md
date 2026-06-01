# Module 18: Active Directory II Lab

### Task 1: Mapping the Domain with BloodHound
1. Run `SharpHound.exe` on a domain-joined machine.
2. Upload the data to BloodHound.
3. Find a path from your current low-privilege user to a "Domain Admin".
4. Document every "hop" (e.g., User $\rightarrow$ Group $\rightarrow$ Computer $\rightarrow$ Admin).

### Task 2: Pass-the-Hash
1. Use Mimikatz to dump the NTLM hash of a local administrator: `sekurlsa::logonpasswords`.
2. Use `impacket-psexec` with that hash to gain a shell on another machine in the domain.

### Task 3: The Golden Ticket
1. Use Mimikatz to extract the hash of the **KRBTGT** account from the Domain Controller.
2. Forge a Golden Ticket for the "Administrator" user.
3. Use the ticket to access a restricted file share on any machine in the domain.

### Task 4: Lateral Movement
1. Use `bloodhound` to find a machine where a Domain Admin is currently logged in.
2. Use `Mimikatz` on that machine to steal the Admin's token.
3. Impersonate the Admin to execute commands on the Domain Controller.
