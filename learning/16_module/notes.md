# Module 16: Wireless Hacking (Wi-Fi)

## 1. Introduction to 802.11
Wireless hacking is different from network hacking because you are attacking the **radio waves** (the Physical Layer).

### The Three Main Security Types:
- **WEP (Wired Equivalent Privacy)**: Extremely old, can be cracked in minutes.
- **WPA2 (Wi-Fi Protected Access 2)**: The current standard. Uses a "4-Way Handshake" to authenticate.
- **WPA3**: The newest standard; much more resistant to offline attacks.

## 2. The 4-Way Handshake
To crack WPA2, you don't attack the router directly; you attack the **Handshake**.
When a device (Client) connects to a Router (AP), they exchange 4 packets. This handshake contains a "hashed" version of the password.
- **The Strategy**: Capture the handshake $\rightarrow$ Take it offline $\rightarrow$ Brute-force the hash using a wordlist.

## 3. Common Attack Vectors

### A. Deauthentication (Deauth)
Sending a special "deauth" packet to a client to force them to disconnect from the Wi-Fi. When they reconnect automatically, you capture the 4-way handshake.

### B. Evil Twin
Creating a fake Wi-Fi access point with the same name (SSID) as the target. Users connect to your fake AP, and you capture their credentials via a fake login page (Captive Portal).

### C. WPS (Wi-Fi Protected Setup)
A feature allowing connection via a 8-digit PIN. This PIN can be brute-forced using tools like **Reaver**.

## 4. Hardware Requirements
You cannot hack Wi-Fi with a standard laptop card. You need a USB Wi-Fi adapter that supports:
- **Monitor Mode**: Ability to listen to all packets in the air, even if they aren't for you.
- **Packet Injection**: Ability to send "fake" packets (like deauth packets).
- **Suggested Chipsets**: Atheros AR9271, Realtek RTL8812AU.
