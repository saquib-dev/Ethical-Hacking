# Module 2: Active Reconnaissance

## What is Active Recon?
Active reconnaissance involves interacting with the target system to find open ports and services. 
**Warning**: This can be detected by Firewalls and Intrusion Detection Systems (IDS).

## Core Tools:
1. **Nmap**: The gold standard for network scanning.
2. **Dirsearch / Gobuster**: Finding hidden folders on a website (e.g., `/admin` or `/config`).
3. **Nikto**: A web server scanner that looks for common misconfigurations.

## The Goal
The goal is to create a "Map" of the target:
- Which ports are open?
- What software is running on those ports?
- What version of the software is it? (Very important for finding exploits).
