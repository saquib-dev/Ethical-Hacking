# Wireshark & TShark Commands Cheat Sheet

*Note: While Wireshark is primarily a GUI tool, `tshark` is its command-line equivalent.*

## TShark Basic Commands
```bash
# List available interfaces
tshark -D

# Capture traffic on a specific interface
tshark -i eth0

# Capture and save to a pcap file
tshark -i eth0 -w capture.pcap

# Read from a pcap file
tshark -r capture.pcap
```

## Capture Filters (Used when starting a capture)
```text
# Capture only HTTP traffic
port 80

# Capture traffic to/from a specific IP
host 192.168.1.100

# Capture traffic from a specific source network
src net 192.168.1.0/24

# Capture TCP traffic only
tcp
```

## Display Filters (Used in Wireshark GUI or TShark when reading)
```text
# Show only HTTP GET requests
http.request.method == "GET"

# Show traffic for a specific IP address
ip.addr == 192.168.1.100

# Show traffic going to a specific destination port
tcp.dstport == 443

# Filter by a specific protocol
dns

# Combine filters (e.g., HTTP traffic to a specific IP)
http and ip.dst == 192.168.1.50

# Find a specific string in packet bytes
frame contains "password"
```

## Useful TShark Extraction Commands
```bash
# Extract HTTP host and URI
tshark -r capture.pcap -Y "http.request" -T fields -e http.host -e http.request.uri

# Extract DNS queries
tshark -r capture.pcap -Y "dns.flags.response == 0" -T fields -e dns.qry.name
```
