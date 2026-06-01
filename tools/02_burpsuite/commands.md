# Burp Suite Essential Workflows & Shortcuts

*Note: Burp Suite is primarily a GUI-based tool, so this cheat sheet focuses on key workflows and keyboard shortcuts rather than CLI commands.*

## Key Shortcuts (Default)
- **Send to Repeater:** `Ctrl + R` (Cmd + R on Mac)
- **Send to Intruder:** `Ctrl + I` (Cmd + I on Mac)
- **Forward intercepted request:** `Ctrl + F`
- **Toggle interception:** Disable/Enable via the Proxy > Intercept tab.

## Core Modules
### Proxy
- **Function:** Intercepts, inspects, and modifies traffic between the browser and target.
- **Workflow:** Set browser proxy to `127.0.0.1:8080`. Install PortSwigger CA certificate in the browser to intercept HTTPS traffic.

### Repeater
- **Function:** Manually manipulate and reissue individual HTTP requests.
- **Workflow:** Right-click a request in Proxy history -> Send to Repeater. Modify parameters, headers, or body and click 'Send' to analyze the response.

### Intruder
- **Function:** Automated customized attacks against web applications.
- **Attack Types:**
  - *Sniper:* Iterates through payloads placing them into single payload positions one at a time.
  - *Battering ram:* Uses a single payload set and places the payload in all positions simultaneously.
  - *Pitchfork:* Uses multiple payload sets, iterating through them simultaneously.
  - *Cluster bomb:* Uses multiple payload sets, iterating through all possible combinations.

### Decoder
- **Function:** Encode or decode data (URL, HTML, Base64, Hex, etc.) and generate hashes.

### Comparer
- **Function:** Perform a visual "diff" between two items of data (e.g., responses from a successful vs. failed login).
