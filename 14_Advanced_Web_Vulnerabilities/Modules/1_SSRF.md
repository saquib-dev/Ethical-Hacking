# Module 1: SSRF (Server Side Request Forgery)

## What is SSRF?
SSRF happens when an attacker can trick a server into making a request to a location it shouldn't.
Example: A website has a feature "Fetch image from URL". An attacker gives it `http://localhost/admin` or `http://169.254.169.254` (cloud metadata).

## Impact:
- **Internal Scanning**: Scanning the company's internal network from the server.
- **Cloud Credential Theft**: Stealing AWS/Azure tokens from the internal metadata service.
- **Bypassing Firewalls**: Accessing services that are only open to "localhost".
