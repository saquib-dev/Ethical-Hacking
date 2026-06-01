# Module 01: Practical Examples in Lab Setup

## 1. Practical Host-Only Network Configuration

When setting up your hacking lab, configuring the network correctly is critical to ensure your vulnerable machines are not exposed to your real home network.

Imagine you are using VirtualBox. Here is how your setup might look using a **Host-Only Network**:

### The Setup
- **Host Machine (Your Physical PC):** `192.168.1.100` (Home network IP)
- **Virtual Network Adapter (Host-Only):** `192.168.56.1` (Created by the Hypervisor)

### The Virtual Machines (VMs)
1. **Attacker VM (Kali Linux):** 
   - Network Mode: Host-Only
   - IP Address: `192.168.56.10`
2. **Victim VM (Metasploitable 2):** 
   - Network Mode: Host-Only
   - IP Address: `192.168.56.11`

### How It Works in Practice
- Kali (`.10`) can ping and attack Metasploitable (`.11`) because they are on the same isolated subnet.
- Your physical PC (`.1`) can also communicate with them.
- However, if the Victim VM is infected with a highly aggressive malware worm during your testing, it **cannot** route traffic out to your home network (like your TV or phone) or to the internet. It is contained within the `192.168.56.0/24` subnet.

## 2. Taking and Reverting Snapshots

Snapshots are a hacker's safety net. Here is a practical workflow:

1. **Clean Slate:** You install a fresh Windows 10 VM to test malware.
2. **Take Snapshot:** You name the snapshot "Clean Install - Pre-Infection".
3. **Execution:** You run a malicious script inside the VM. It encrypts all files and destroys the bootloader (Ransomware).
4. **Revert:** You click "Restore Snapshot" in your hypervisor. Within 10 seconds, the VM is restored to its exact state prior to running the malware, completely clean and ready for the next test.
