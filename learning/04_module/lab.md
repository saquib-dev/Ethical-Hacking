# Module 04: Nmap Practical Lab

### Task 1: Local Network Mapping
1. Run a ping sweep of your current network to find active devices:
   `nmap -sn 192.168.1.0/24` (Replace with your actual subnet).
2. Pick one active IP (that you own!) and perform a basic scan:
   `nmap <target_ip>`

### Task 2: Service Fingerprinting
1. Scan the target `scanme.nmap.org` (provided by Nmap for testing).
2. Run a version scan: `nmap -sV scanme.nmap.org`.
3. Which version of the service is running on port 22? Write it down.

### Task 3: The Thorough Scan
1. Run an aggressive scan on your target:
   `sudo nmap -A <target_ip>`
2. Analyze the output:
   - What is the guessed OS?
   - What services are open?
   - Did Nmap find any interesting scripts?

### Task 4: Comparison Study
1. Scan a target using `-sT` (Connect scan).
2. Scan the same target using `-sS` (SYN scan).
3. Note the difference in speed and the output.
