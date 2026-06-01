# Module 07: Web Analysis Commands

### 1. Command Line Web Tools
| Command | Description | Use Case |
| :--- | :--- | :--- |
| `curl -I <url>` | Fetch only the HTTP headers | Check server version and cookies. |
| `curl -X POST -d "user=admin" <url>` | Send a POST request | Test a login form without a browser. |
| `wget <url>` | Download a file/page | Save a page for offline analysis. |

### 2. Burp Suite: The Industry Standard
Burp Suite is a **Proxy**. It sits between your browser and the server, allowing you to stop a request, change the data, and then send it.

**Key Burp Tabs:**
- **Proxy**: Intercept and modify requests in real-time.
- **Repeater**: Send the same request multiple times with slight changes.
- **Intruder**: Automate attacks (e.g., brute-force a password).
- **Decoder**: Convert Base64, URL encoding, or Hex.

### The "Web Analysis Chain" (Example):
Intercept a request $\rightarrow$ Change a user ID $\rightarrow$ See if you can access another user's profile:
```bash
# Example using curl to test a parameter
curl "http://target.com/profile?id=1" 
curl "http://target.com/profile?id=2"
```
