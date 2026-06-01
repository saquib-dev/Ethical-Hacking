# Nmap Essential Commands & Cheat Sheet

## Basic Scans
- **Ping Scan:** `nmap -sn <target>` (Determine which hosts are up)
- **Quick Scan:** `nmap -F <target>` (Scans the top 100 ports)
- **Default Scan:** `nmap <target>` (Scans the top 1000 ports)
- **All Ports Scan:** `nmap -p- <target>` (Scans all 65535 ports)

## Detailed Scans
- **TCP Connect Scan:** `nmap -sT <target>` (Completes the 3-way handshake)
- **SYN Stealth Scan:** `nmap -sS <target>` (Half-open scan, requires root)
- **UDP Scan:** `nmap -sU <target>` (Scans UDP ports)

## Service & OS Detection
- **Service Version Detection:** `nmap -sV <target>` (Probes open ports to determine service/version info)
- **OS Detection:** `nmap -O <target>` (Attempts to determine the operating system)
- **Aggressive Scan:** `nmap -A <target>` (Enables OS detection, version detection, script scanning, and traceroute)

## Timing & Performance
- **Paranoid to Insane:** `nmap -T0` to `-T5` (Adjusts scan speed; T4 is typically recommended for standard networks)

## Nmap Scripting Engine (NSE)
- **Default Scripts:** `nmap -sC <target>`
- **Specific Script:** `nmap --script <script_name> <target>`
- **Vulnerability Scan:** `nmap --script vuln <target>`

## Output Options
- **Normal Output:** `-oN normal.txt`
- **Grepable Output:** `-oG grepable.txt`
- **XML Output:** `-oX output.xml`
- **All Formats:** `-oA output_all`
