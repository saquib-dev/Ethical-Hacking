# Burp Suite Practical Lab

## Scenario: Authentication Bypass & Parameter Tampering
You are testing a web application's login portal and subsequent profile update page. The goal is to identify if the application is vulnerable to brute-force attacks and if it suffers from Insecure Direct Object Reference (IDOR).

## Objective
Bypass the login mechanism using Intruder and attempt to view another user's profile using Repeater.

## Tasks
1. **Proxy Setup & Interception:**
   - Configure your browser to route traffic through Burp Suite.
   - Navigate to the login page and enable "Intercept is on" in Burp Proxy.
   - Submit dummy credentials (e.g., `admin` / `password`).

2. **Brute-Forcing with Intruder:**
   - Send the intercepted login request to Intruder (`Ctrl + I`).
   - Go to the Intruder tab, clear all payload positions, and highlight the password value. Add a payload position (`§password§`).
   - Select "Sniper" attack type.
   - Under the Payloads tab, load a small list of common passwords.
   - Start the attack and analyze the results. Sort by "Length" or "Status" to identify the successful login response.

3. **Parameter Tampering with Repeater:**
   - Once authenticated, navigate to the user profile page. Intercept the request.
   - Send this request to Repeater (`Ctrl + R`).
   - Notice the URL parameter (e.g., `?user_id=101`).
   - In Repeater, change the `user_id` to `102` and click Send.
   - Analyze the response to determine if you have successfully accessed another user's data (IDOR).

## Review
Document the vulnerabilities found. Note the exact payload that successfully bypassed the login and the HTTP response differences that confirmed the IDOR vulnerability.
