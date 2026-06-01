# Module 01: Virtual Machine & Lab Setup

## 1. Understanding Virtualization
Virtualization allows you to run multiple "guest" operating systems (VMs) on a single "host" physical machine. 

### Why this is essential for Hacking:
- **Safety**: If you accidentally run a malicious script or crash the OS, your actual computer (the host) remains untouched.
- **Snapshots**: You can save a "state" of your machine. If you break the configuration, you can "revert" to the snapshot in seconds.
- **Lab Creation**: You can run a "Victim VM" (like Metasploitable) and an "Attacker VM" (Kali) on the same machine and let them talk to each other.

## 2. Hypervisors
A hypervisor is the software that manages VMs.
- **Type 2 Hypervisors**: Installed on top of an OS (e.g., VirtualBox, VMware Workstation). These are best for learners.
- **Type 1 Hypervisors**: Installed directly on the hardware (e.g., ESXi, Proxmox). Used in professional data centers.

## 3. Networking Modes (The Most Important Part)
Getting the network wrong is the #1 reason beginners fail their labs.

| Mode | Description | Use Case |
| :--- | :--- | :--- |
| **NAT** | VM shares the host's IP. Can access internet. | Basic updates, browsing. |
| **Bridged** | VM gets its own IP from your router. | Testing devices on your actual home network. |
| **Host-Only** | VM can only see the host and other VMs. | High-security labs; prevents malware from escaping. |
| **Internal** | VMs can only see each other; no host access. | Isolated attack/defense simulations. |

## 4. Kali Linux Overview
Kali is a Debian-based distribution pre-loaded with hundreds of security tools. It is not designed to be a daily-driver OS; it is a **toolkit**.
