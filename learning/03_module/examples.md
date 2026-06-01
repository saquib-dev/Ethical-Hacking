# Module 03: Practical Examples in Networking

## 1. The TCP 3-Way Handshake in Action

When you visit a website (e.g., `http://192.168.1.100` on port 80), your computer doesn't just immediately send the webpage request. It performs the TCP 3-way handshake first. 

If you were monitoring this traffic with a tool like Wireshark, it would look like this:

1. **Packet 1 (SYN):** Your Computer $\rightarrow$ Web Server
   *Message:* "Hello, I would like to open a connection to Port 80. Are you there?"
2. **Packet 2 (SYN-ACK):** Web Server $\rightarrow$ Your Computer
   *Message:* "Hello! Yes, I am here and Port 80 is open. I acknowledge your request."
3. **Packet 3 (ACK):** Your Computer $\rightarrow$ Web Server
   *Message:* "Great, I acknowledge your response. The connection is established."
   
*(Only after this handshake does your computer actually send the `GET / HTTP/1.1` request to ask for the website's HTML).*

## 2. Interacting with Ports Manually (Netcat)

Hackers often use a tool called `nc` (Netcat) to manually connect to ports and see how they respond. This is called "Banner Grabbing."

**Example: Connecting to an open FTP Port (21)**
```bash
$ nc 10.10.10.5 21
220 (vsFTPd 2.3.4)
```
*Takeaway:* Just by connecting, the server announced it is running `vsFTPd 2.3.4`. A quick Google search reveals this specific version has a famous built-in backdoor vulnerability!

**Example: Connecting to an open SSH Port (22)**
```bash
$ nc 10.10.10.5 22
SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.8
```

## 3. DNS Lookups and Manipulation

A hacker might want to map out an organization's network by checking their DNS records using a tool like `dig`.

```bash
# Asking the DNS server for the IP address of google.com
$ dig google.com +short
142.250.190.46
```
If a hacker is in a Man-in-the-Middle position, they could use **DNS Spoofing** to tell the victim's computer that `google.com` actually points to `192.168.1.50` (the hacker's fake login page). Because DNS operates over UDP (fast, no verification), it is highly susceptible to spoofing.
