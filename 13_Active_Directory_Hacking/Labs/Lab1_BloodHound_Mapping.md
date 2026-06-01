# Lab 1: Mapping the Network with BloodHound

## Goal: Use BloodHound to find the shortest path to Domain Admin.

## What is BloodHound?
BloodHound uses graph theory to map out relationships in AD (e.g., "User A has Admin rights on Computer B, and Computer B has a Session from Domain Admin").

## Steps:
1. **Collect Data**: Use `SharpHound.exe` (on a Windows machine in the domain) to collect data.
2. **Upload to BloodHound**: Import the collected JSON files into the BloodHound GUI.
3. **Analyze**: 
   - Search for "Domain Admins".
   - Use the "Shortest Path to Domain Admin" query.
4. **Identify the Path**: Find which user or computer you need to compromise first to eventually reach the DC.

## Success Check:
- [ ] Successfully imported data into BloodHound.
- [ ] Identified a clear attack path to the Domain Admin.
