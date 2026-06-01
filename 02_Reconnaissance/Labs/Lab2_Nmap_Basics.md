# Lab 2: Nmap Basics

## Goal: Scan a network to find open ports.

## Target for Practice: `scanme.nmap.org` (This is a legal target provided by Nmap).

## Commands to Try:
1. **Simple Scan**: `nmap scanme.nmap.org` (Finds top 1000 ports).
2. **Service Version Detection**: `nmap -sV scanme.nmap.org` (Tells you WHAT is running on the port).
3. **OS Detection**: `nmap -O scanme.nmap.org` (Tries to guess if it's Linux or Windows).
4. **Aggressive Scan**: `nmap -A scanme.nmap.org` (Does everything: OS, Version, Scripts).

## Success Check:
- [ ] Successfully scanned `scanme.nmap.org`.
- [ ] Identified at least one open port.
- [ ] Identified the service version (e.g., Apache 2.4).
