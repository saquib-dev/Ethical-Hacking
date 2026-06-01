# Metasploit & Sliver Mastery Plan (4 Weeks)

Comparing the "Loud" tool (Metasploit) and the "Stealth" tool (Sliver).

## Week 1: Metasploit Basics
- **Goal**: Rapid exploitation.
- **Tasks**:
  - Master `msfconsole` search and usage.
  - Understand the difference between `exploit` and `run`.
  - Configure `LHOST` and `RHOST` correctly.

## Week 2: Advanced Meterpreter
- **Goal**: Post-exploitation power.
- **Tasks**:
  - Use `hashdump` to steal passwords.
  - Use `shell` to enter the OS command line.
  - Implement basic persistence using the `persistence` module.

## Week 3: Sliver C2 Setup
- **Goal**: Stealthy command and control.
- **Tasks**:
  - Install Sliver and set up a listener.
  - Generate `mTLS` and `HTTP` beacons.
  - Manage multiple sessions simultaneously.

## Week 4: Stealth & Pivoting
- **Goal**: Avoiding detection.
- **Tasks**:
  - Use Sliver's `pivots` to route traffic through a beacon.
  - Compare the "noise" of Metasploit vs the "stealth" of Sliver.
  - Practice "Beaconing" intervals to avoid EDR alerts.
