# Module 03: Networking Fundamentals for Hackers

## 1. The OSI Model: The Hacker's Map
The Open Systems Interconnection (OSI) model describes how data moves from one computer to another. Hackers target different layers.

| Layer | Name | Focus | Hacker's Target |
| :--- | :--- | :--- | :--- |
| **7** | **Application** | User Interface | HTTP, DNS, FTP (SQLi, XSS) |
| **6** | **Presentation** | Data Formatting | SSL/TLS, JPEG (Encoding attacks) |
| **5** | **Session** | Connection Mgmt | NetBIOS, RPC (Session Hijacking) |
| **4** | **Transport** | End-to-End Delivery | TCP/UDP (Port scanning) |
| **3** | **Network** | Routing/IP | IP, ICMP (Ping sweeps, Spoofing) |
| **2** | **Data Link** | Local Switching | MAC Addresses (ARP Spoofing) |
| **1** | **Physical** | Cables/Bits | Hardware, Wi-Fi (Jamming, Sniffing) |

## 2. TCP vs. UDP (The Transport Layer)
*   **TCP (Transmission Control Protocol)**: "Reliable". It uses a **3-way handshake** (SYN $\rightarrow$ SYN-ACK $\rightarrow$ ACK). If a packet is lost, it is resent. Used for Web, Email, SSH.
*   **UDP (User Datagram Protocol)**: "Fast". No handshake. It just sends data and hopes it arrives. Used for Video Streaming, DNS, Gaming.

## 3. IP Addressing & DNS
*   **IPv4**: 32-bit address (e.g., `192.168.1.1`).
*   **MAC Address**: The unique hardware ID of your network card.
*   **DNS (Domain Name System)**: The "Phonebook" of the internet. It turns `google.com` $\rightarrow$ `142.250.190.46`. Attackers use **DNS Poisoning** to redirect users to fake sites.

## 4. Common Ports to Memorize
If you see these ports open, here is what is likely running:
- **21**: FTP (File Transfer)
- **22**: SSH (Secure Shell - Remote Access)
- **25**: SMTP (Email)
- **53**: DNS (Domain Name System)
- **80**: HTTP (Web)
- **443**: HTTPS (Secure Web)
- **445**: SMB (Windows File Sharing - *Huge target for exploits*)
- **3389**: RDP (Windows Remote Desktop)
