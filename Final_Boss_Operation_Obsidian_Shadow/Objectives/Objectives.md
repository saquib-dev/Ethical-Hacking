# Mission Objectives (Professional Edition)

To complete Operation: Obsidian Shadow, you must achieve the following in order. **Note: The target now has basic AV and EDR active.**

## Phase 1: The Stealthy Breach
- [ ] Perform reconnaissance.
- [ ] Find a web vulnerability.
- [ ] **Advanced Task**: Write a custom Python script to automate the exploitation.
- [ ] **Stealth Task**: Obfuscate your payload to bypass the web server's basic security filters.
- [ ] Gain a low-privilege shell.

## Phase 2: The Invisible Pivot
- [ ] Establish a C2 connection using **Sliver** instead of a simple reverse shell.
- [ ] Use the C2 beacon to scan the internal network.
- [ ] Exploit an API vulnerability to steal user credentials.

## Phase 3: Domain Domination
- [ ] Enter the AD environment.
- [ ] Use BloodHound to map the path to Domain Admin.
- [ ] Perform a Kerberos attack to escalate privileges.
- [ ] **Stealth Task**: Use "Living off the Land" (LotL) techniques to move laterally without triggering EDR alerts.

## Phase 4: The Container Breakout
- [ ] Find a Docker container running a critical service on the DC.
- [ ] Perform a **Container Escape** to gain root access to the underlying Host OS.

## Phase 5: The Binary Secret
- [ ] Find the security binary on the Host.
- [ ] Reverse engineer the binary in Ghidra to find the hardcoded Cloud Access Key.

## Phase 6: The Cloud Vault
- [ ] Use the stolen keys to access the AWS S3 bucket.
- [ ] Download the **Obsidian Key**.

## Phase 7: The Professional Report
- [ ] Document the entire attack chain.
- [ ] Include the custom scripts you wrote.
- [ ] Provide remediation steps that address both the bug and the detection failure.
