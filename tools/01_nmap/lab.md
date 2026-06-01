# Nmap Practical Lab

## Scenario: Network Discovery and Vulnerability Assessment
You are tasked with assessing the security posture of a newly deployed subnet (192.168.1.0/24) before it is moved into production. You must identify live hosts, discover open ports, and fingerprint the running services.

## Objective
Map the network and document all listening services and their versions.

## Tasks
1. **Host Discovery:**
   - Run a ping sweep to identify active hosts without port scanning.
   - *Command:* `nmap -sn 192.168.1.0/24`

2. **Port Scanning:**
   - Select one active host (e.g., 192.168.1.15) and perform a full TCP port scan to ensure no non-standard ports are missed.
   - *Command:* `nmap -p- 192.168.1.15`

3. **Service Fingerprinting:**
   - Once open ports are identified, run an aggressive scan against the target to enumerate OS details and service versions.
   - *Command:* `nmap -A -p <open_ports> 192.168.1.15`

4. **Vulnerability Scanning:**
   - Utilize the Nmap Scripting Engine to check for common vulnerabilities on the target.
   - *Command:* `nmap --script vuln 192.168.1.15`

5. **Documentation:**
   - Save the results in all formats for further analysis.
   - *Command:* `nmap -A -p- 192.168.1.15 -oA nmap_report`

## Review
Analyze the `nmap_report.nmap` file to identify any outdated software versions or exposed administrative interfaces that could be leveraged for exploitation.
