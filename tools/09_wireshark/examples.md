# Wireshark / TShark Examples

## Scenario: Analyzing HTTP Traffic for Cleartext Credentials
During a network audit, you may need to analyze a packet capture to identify insecure protocols and data being transmitted without encryption.

**Command:**
```bash
tshark -r network_traffic.pcap -Y "http.request.method == POST" -T fields -e ip.src -e http.file_data
```

**Mocked Output:**
```text
192.168.1.105    username=admin&password=Password123!
192.168.1.202    user=test&pass=test
```

**Explanation:**
- `-r network_traffic.pcap`: Read the specified capture file.
- `-Y "http.request.method == POST"`: Apply a display filter to show only HTTP POST requests.
- `-T fields`: Change the output format to display specific fields instead of the full packet summary.
- `-e ip.src -e http.file_data`: Extract and display the source IP address and the HTTP payload data (which often contains form submissions like credentials).
