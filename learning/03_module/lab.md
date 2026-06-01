# Module 03: Networking Lab

### Task 1: Local Network Discovery
1. Find your own IP address and MAC address using `ip addr`.
2. Ping your gateway (your router) to ensure connectivity.
3. Use `arp -a` to see other devices your computer has recently communicated with on the local network.

### Task 2: DNS Deep Dive
1. Use `nslookup` to find the IP address of `github.com`.
2. Use `dig` to find the **MX records** (Mail Exchange) for `google.com`. This tells you which servers handle their email.
3. Use `traceroute` to see how many "hops" (routers) your data passes through to reach `8.8.8.8`.

### Task 3: Netcat Basics
1. Open two terminal windows.
2. In **Terminal A**, start a listener: `nc -lvnp 1234`.
3. In **Terminal B**, connect to that listener: `nc 127.0.0.1 1234`.
4. Type a message in Terminal B and see it appear in Terminal A. (You have just created a basic chat app/backdoor!).
