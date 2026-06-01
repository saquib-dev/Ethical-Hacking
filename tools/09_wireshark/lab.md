# Lab: Network Traffic Analysis with Wireshark

## Scenario
You have been provided with a packet capture file (`suspicious_activity.pcap`) from a compromised network. Your task is to analyze the capture to identify the attacker's actions and any compromised data.

## Objectives
1. Analyze a pcap file using Wireshark display filters.
2. Identify cleartext credentials traversing the network.
3. Extract transferred files from the capture.

## Steps
1. **Open the Capture:** Open `suspicious_activity.pcap` in Wireshark.
2. **Initial Inspection:** Look at the Protocol Hierarchy Statistics (Statistics -> Protocol Hierarchy) to get an overview of the traffic types.
3. **Filter for HTTP:** Apply the display filter `http` to view only web traffic.
4. **Find Credentials:**
   - Look for HTTP POST requests, often used for login forms.
   - Apply filter: `http.request.method == "POST"`
   - Inspect the packet details (specifically HTML Form URL Encoded or similar sections) to find usernames and passwords.
5. **Analyze FTP/Telnet:** Cleartext protocols are vulnerable. Filter by `ftp` or `telnet` to see if any sensitive data was transmitted without encryption. Follow the TCP stream (Right-click packet -> Follow -> TCP Stream) to view the entire conversation.
6. **Extract Files:** If files were downloaded via HTTP or FTP, you can extract them.
   - Go to File -> Export Objects -> HTTP (or FTP).
   - Select the file and click "Save".

## Conclusion
You successfully analyzed network traffic to identify insecure protocols, extract compromised credentials, and reconstruct files transferred during the capture period.
