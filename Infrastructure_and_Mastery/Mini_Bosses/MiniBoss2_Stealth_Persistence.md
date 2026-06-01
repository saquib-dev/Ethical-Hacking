# Mini-Boss 2: The Invisible Ghost

## Goal: Deploy a payload that survives a reboot and avoids AV.

## The Challenge:
You have access to a Windows VM.
- Install Windows Defender (on).
- Create a reverse shell that is **not** detected by Defender.
- Set up persistence so that when you reboot the VM, you get a connection back within 2 minutes.

## Success Criteria:
- [ ] Payload is not flagged by Windows Defender.
- [ ] Connection is established automatically after reboot.
- [ ] You used a "Living off the Land" technique (e.g., Registry or Scheduled Task).
