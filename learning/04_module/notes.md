# Module 04: Network Scanning with Nmap

## 1. What is Scanning?
Scanning is the "Active Reconnaissance" phase. The goal is to move from knowing a target exists to knowing exactly **what is running on it**.

### The Goal of a Scan:
- Is the host alive?
- Which ports are open?
- What services are running on those ports? (e.g., Apache 2.4.41)
- What is the Operating System? (e.g., Ubuntu 20.04)

## 2. The TCP Three-Way Handshake & Scanning
Nmap uses different methods to determine if a port is open:

### TCP SYN Scan (`-sS`) - "The Stealth Scan"
1. Attacker sends **SYN**.
2. Target sends **SYN-ACK** (Port is open).
3. Attacker sends **RST** (Reset) instead of ACK.
*The connection is never fully established, so many old logs won't record it.*

### TCP Connect Scan (`-sT`)
1. Attacker sends **SYN**.
2. Target sends **SYN-ACK**.
3. Attacker sends **ACK**.
*Full connection. Very loud and easily detected by Firewalls/IDS.*

### UDP Scan (`-sU`)
UDP doesn't have a handshake. Nmap sends a packet; if no response comes back, it's "open|filtered". If an "ICMP Port Unreachable" comes back, it's closed.

## 3. Scanning States
- **Open**: A service is listening and accepting connections.
- **Closed**: No service is listening, but the host responded.
- **Filtered**: A firewall is blocking the probes; Nmap can't tell if it's open or closed.
