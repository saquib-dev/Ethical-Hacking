# Module 03: Networking Commands

### 1. Basic Connectivity
| Command | Description | Usage |
| :--- | :--- | :--- |
| `ping <target>` | Check if host is alive | `ping -c 4 8.8.8.8` |
| `traceroute <target>` | See the path to target | `traceroute google.com` |
| `ip addr` | View your local IP/MAC | `ip addr show` |

### 2. DNS Exploration
| Command | Description | Usage |
| :--- | :--- | :--- |
| `nslookup <domain>` | Simple DNS query | `nslookup kali.org` |
| `dig <domain>` | Detailed DNS info | `dig google.com ANY` |
| `host <domain>` | Quick IP lookup | `host google.com` |

### 3. Port & Connection Analysis
| Command | Description | Usage |
| :--- | :--- | :--- |
| `netstat -tunlp` | See listening ports | `sudo netstat -tunlp` |
| `ss -tulpn` | Modern replacement for netstat | `sudo ss -tulpn` |
| `arp -a` | View the ARP cache | See other devices on local net. |

### 4. The "Hacker's Connection" (Netcat)
**Netcat (`nc`)** is the "Swiss Army Knife" of networking.
- **Listen for a connection**: `nc -lvnp 4444` (Listen, Verbose, Numeric, Port 4444)
- **Connect to a port**: `nc <target_ip> 80`
