# BloodHound - Notes

## Overview
BloodHound is a Single Page Application (SPA) web application heavily relying on graph theory to reveal the hidden and often unintended relationships within an Active Directory (AD) or Azure environment. Attackers use it to identify highly complex attack paths that would otherwise be impossible to quickly identify manually.

## How it Works
BloodHound consists of three main components:
1. **Data Collector (Ingestor):** Tools like `SharpHound` (C#) or `BloodHound.py` (Python) query Domain Controllers to collect directory data (users, groups, computers, ACLs, sessions).
2. **Database:** A Neo4j graph database that stores the collected data as nodes and edges.
3. **GUI:** The Electron-based graphical interface used to visualize the graph and query for attack paths (e.g., "Find Shortest Path to Domain Admins").

## Key Concepts
- **Nodes:** Represent objects in AD (Users, Groups, Computers, Domains, GPOs).
- **Edges:** Represent relationships or permissions between nodes (e.g., `MemberOf`, `HasSession`, `AdminTo`, `GenericAll`, `ForceChangePassword`).
- **Derivative Local Admin:** The concept of gaining admin access to a machine to harvest credentials of an administrator of another machine, chaining these together to reach a high-value target.

## Defensive Uses (BlueHound)
Defenders use BloodHound to:
- Identify and eliminate unintended privilege escalation paths.
- Audit Tiered Administration models.
- Find anomalous or dangerous ACL configurations.
