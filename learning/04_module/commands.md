# Module 04: Nmap Command Reference

### 1. Basic Scans
| Command | Description | When to use |
| :--- | :--- | :--- |
| `nmap <target>` | Scans top 1000 ports | Fast initial check. |
| `nmap -p 80,443 <target>` | Scan specific ports | When you only care about web. |
| `nmap -p- <target>` | Scan all 65,535 ports | Thorough search for "hidden" services. |

### 2. Stealth & Discovery
| Command | Description | Note |
| :--- | :--- | :--- |
| `nmap -sS <target>` | SYN Stealth Scan | Best default scan. |
| `nmap -sT <target>` | TCP Connect Scan | Use if you don't have root/sudo. |
| `nmap -sn <range>` | Ping Sweep | Find active hosts in a subnet. |

### 3. Service & OS Detection
| Command | Description | Example |
| :--- | :--- | :--- |
| `nmap -sV <target>` | Service Version Detection | `nmap -sV 192.168.1.10` |
| `nmap -O <target>` | OS Fingerprinting | Guess the OS version. |
| `nmap -A <target>` | "Aggressive" Scan | Combines `-sV`, `-O`, and scripts. |

### 4. Performance Tuning
- `-T0` to `-T5`: Timing templates. `-T4` is recommended for fast, stable networks. `-T2` is for stealth.
- `--open`: Only show ports that are actually open.

### The "Golden" Nmap Command for Beginners:
```bash
sudo nmap -sS -sV -O -T4 -p- <target_ip>
```
*(Stealth, Version detection, OS detection, Fast, All ports)*
