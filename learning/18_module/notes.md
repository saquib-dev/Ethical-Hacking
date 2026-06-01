# Module 18: Active Directory II (Advanced Attacks)

## 1. BloodHound: Visualizing the Attack Path
In large AD environments, it's impossible to track permissions manually. **BloodHound** uses graph theory to find the shortest path to Domain Admin.

### How BloodHound Works:
1. **SharpHound**: A collector tool run on a domain machine. It gathers all users, groups, computers, and permissions.
2. **BloodHound GUI**: You upload the JSON data. The tool then shows you "paths."
   - *Example*: User A $\rightarrow$ member of Group B $\rightarrow$ has GenericWrite over User C $\rightarrow$ is Domain Admin.

## 2. Golden Tickets vs. Silver Tickets

### A. Golden Tickets (Total Domain Control)
A Golden Ticket is a forged TGT (Ticket Granting Ticket). It is created by stealing the hash of the **KRBTGT** account (the account that encrypts all tickets in the domain).
- **Impact**: You can impersonate **any user** and access **any resource** for years, even if the user changes their password.

### B. Silver Tickets (Resource Control)
A Silver Ticket is a forged Service Ticket (TGS). It is created by stealing the password hash of a specific service account.
- **Impact**: You can access that specific service (e.g., the file server) but cannot request other tickets from the DC.

## 3. Pass-the-Hash (PtH)
In Windows, you don't actually need the clear-text password to authenticate; you only need the **NTLM hash**.
- **The Attack**: If you steal the hash of an admin from memory (using Mimikatz), you can use that hash to authenticate to other machines without ever knowing the password.
