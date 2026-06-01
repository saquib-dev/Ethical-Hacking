# Module 2: Professional C2 Tools

## Sliver
A modern, open-source C2 framework written in Go. It is highly powerful and used by many Red Teams.
- **Features**: mTLS encryption, DNS beacons, and cross-platform support.

## Cobalt Strike
The "Industry Standard" for corporate penetration testing. (Paid).
- **Features**: Beaconing, "Screamer" payloads, and advanced lateral movement.

## Empire
A PowerShell-focused C2. Great for Windows environments.

## Choosing a C2:
The choice depends on the target. If the target has heavy monitoring, you use a C2 that supports **DNS Tunneling** (sending data inside DNS requests), which is almost impossible to block.
