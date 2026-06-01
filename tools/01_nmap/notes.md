# Nmap Theoretical Overview & Best Practices

## What is Nmap?
Nmap (Network Mapper) is a free, open-source utility for network discovery and security auditing. It uses raw IP packets in novel ways to determine what hosts are available on the network, what services (application name and version) those hosts are offering, what operating systems (and OS versions) they are running, what type of packet filters/firewalls are in use, and dozens of other characteristics.

## How it Works
- **Host Discovery:** Primarily uses ICMP echo requests, TCP SYN to port 443, TCP ACK to port 80, and ICMP timestamp requests to verify if a host is alive.
- **Port Scanning:** Sends specific packets to target ports and analyzes the responses. 
  - *Open:* Application is actively accepting TCP connections, UDP datagrams, or SCTP associations.
  - *Closed:* Accessible but no application is listening.
  - *Filtered:* Nmap cannot determine whether the port is open because packet filtering prevents its probes from reaching the port.
- **Service Fingerprinting:** Sends a series of probes to open ports and compares the responses to a massive database of known service fingerprints (nmap-service-probes).

## Best Practices
1. **Authorization:** NEVER scan networks or hosts without explicit, written permission. Unauthorized scanning can be illegal.
2. **Stealth and Impact:** Be mindful of scan intensity. Using `-T5` can overwhelm older network equipment or trigger Intrusion Detection Systems (IDS). Use slower timing (`-T2` or `-T3`) for stealth.
3. **Target Scope:** Always double-check your target IP or CIDR range before initiating a scan to avoid accidental out-of-scope scanning.
4. **Iterative Approach:** Start with broad, fast scans (e.g., host discovery), then narrow down to detailed scans (service/version) on discovered hosts to save time and bandwidth.
5. **Update NSE:** Keep the Nmap Scripting Engine database updated to ensure you have the latest vulnerability checks.
