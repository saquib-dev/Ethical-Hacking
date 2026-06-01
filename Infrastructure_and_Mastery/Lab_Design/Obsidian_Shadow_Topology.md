# Lab Environment Specification: Operation Obsidian Shadow

This document provides the technical specifications required to build the "Final Boss" environment.

## 1. Hardware Requirements (Host Machine)
- **RAM**: Minimum 16GB (32GB recommended).
- **CPU**: Quad-core or higher with Virtualization enabled (VT-x/AMD-V).
- **Storage**: 100GB+ SSD space.

## 2. Virtualization Software
- **VirtualBox** or **VMware Workstation Player**.

## 3. VM Specifications

### VM 1: Attacker Machine (The Shadow)
- **OS**: Kali Linux (Latest)
- **RAM**: 4GB
- **Network**: Bridged or NAT (Internet access required).
- **Key Software**: Burp Suite, Sliver, BloodHound, Ghidra, Impacket, Hashcat.

### VM 2: The Perimeter (Web Server)
- **OS**: Ubuntu Server 22.04
- **RAM**: 2GB
- **Network**: Dual NIC (NIC 1: Public/Host-only, NIC 2: Internal DMZ).
- **Software**: Apache2, PHP 8.x, MySQL.
- **Vulnerabilities to configure**: 
  - Unrestricted file upload in `/uploads` directory.
  - SSRF vulnerability in the `?url=` parameter.

### VM 3: The Internal API (API Server)
- **OS**: Debian 11
- **RAM**: 2GB
- **Network**: Internal DMZ (No public access).
- **Software**: Python Flask API.
- **Vulnerabilities to configure**:
  - BOLA (Broken Object Level Authorization) on `/api/v1/user/<id>`.

### VM 4: The Corporate Core (Domain Controller)
- **OS**: Windows Server 2019/2022
- **RAM**: 4GB
- **Network**: Internal Core (Only accessible from API Server).
- **Roles**: AD DS, DNS.
- **Vulnerabilities to configure**:
  - A service account with a weak password (for Kerberoasting).
  - A "Security Binary" placed in `C:\Security\checker.exe`.
  - A Docker container running in `--privileged` mode.

### VM 5: The Corporate Workstation
- **OS**: Windows 10/11
- **RAM**: 4GB
- **Network**: Internal Core.
- **Software**: Standard office apps.

## 4. Network Topology

```text
[ INTERNET ] 
      |
      v
[ Attacker VM ] ----> [ Web Server (DMZ) ] 
                              |
                              v
                      [ API Server (DMZ) ] 
                              |
                              v
                      [ Domain Controller ] <---> [ Workstation ]
                              |
                              v
                      [ Cloud Mock (S3) ]
```

## 5. Cloud Simulation
To avoid cost and risk, use **LocalStack** (AWS Cloud Mock) on the Attacker VM or a separate small Linux VM.
- **Service**: S3.
- **Bucket Name**: `securecorp-vault-secret`.
- **Permissions**: Restrict access to the specific IAM key found in the DC binary.
