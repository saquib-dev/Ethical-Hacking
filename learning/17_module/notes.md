# Module 17: Active Directory I (The Basics of Windows Domains)

## 1. What is Active Directory (AD)?
Active Directory is a directory service developed by Microsoft for Windows domain networks. It allows administrators to manage permissions and access to networked resources centrally.

### Key AD Components:
- **Domain Controller (DC)**: The server that manages the AD database. It handles authentication (logging in).
- **Forest**: The highest level of organization. A forest contains one or more domains.
- **Organizational Unit (OU)**: A container within a domain used to organize users, groups, and computers.
- **Group Policy Object (GPO)**: A set of rules applied to users or computers (e.g., "Disable USB ports for all users in the HR OU").

## 2. Kerberos: The Heart of AD Authentication
AD uses a protocol called **Kerberos** for authentication. Instead of sending passwords over the network, it uses **Tickets**.

### The Ticket Process:
1. **AS-REQ**: User asks the Key Distribution Center (KDC) for a Ticket Granting Ticket (TGT).
2. **TGT**: The KDC gives the user a TGT (encrypted with the user's password hash).
3. **TGS-REQ**: The user presents the TGT to request a Service Ticket (TGS) for a specific resource (e.g., a file share).
4. **TGS**: The KDC gives the user a Service Ticket.
5. **Access**: The user presents the Service Ticket to the resource server to gain access.

## 3. Initial AD Attack Vectors

### A. AS-REP Roasting
Occurs when a user has "Do not require Kerberos preauthentication" enabled. An attacker can request an AS-REP for that user and crack the encrypted part offline to get the password.

### B. Kerberoasting
Occurs when a service account (like a SQL server) has a **Service Principal Name (SPN)**. Any domain user can request a service ticket for that account. The ticket is encrypted with the service account's password hash, which can be cracked offline.
