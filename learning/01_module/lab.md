# Module 01: Lab Setup Guide

### Task 1: Install and Import
1. Install **VirtualBox** or **VMware**.
2. Download the **Kali Linux VM Image** (not the ISO) from kali.org.
3. Import the appliance and start the VM.
4. Log in with `kali` / `kali`.

### Task 2: First-Time System Hardening
1. Change your default password:
   - Run `passwd` in the terminal.
   - Enter the current password (`kali`), then enter a new strong password.
2. Update the system using the commands in `commands.md`.

### Task 3: Network Configuration Exercise
1. Set your VM to **NAT** mode. Check if you can ping `google.com`.
2. Switch your VM to **Host-Only** mode. Try to ping `google.com` again. (It should fail).
3. Observe how the IP address changes when switching modes using `ip addr`.

### Task 4: Snapshotting
1. Shut down the VM.
2. Take a snapshot and name it "Clean_Install_Base".
3. Start the VM, delete a critical folder (like `/etc/passwd` — **DO NOT DO THIS ON YOUR HOST!**), and observe the system fail.
4. Revert to the "Clean_Install_Base" snapshot and verify the system is working again.
