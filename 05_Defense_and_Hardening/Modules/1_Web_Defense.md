# Module 1: Web Defense

## How to Stop Web Attacks
The main rule of web security: **Never trust user input.**

## Fixes for Common Attacks:
1. **Stopping SQLi**: Use "Prepared Statements". Instead of putting user text directly in the query, you use a placeholder.
2. **Stopping XSS**: Use "Output Encoding". This turns `<script>` into `&lt;script&gt;` so the browser treats it as text, not code.
3. **Stopping IDOR**: Check permissions on the server. Just because a user is logged in doesn't mean they should be allowed to see `user_id=11`.

## WAF (Web Application Firewall)
A WAF acts like a filter. It looks for common attack patterns (like `' OR 1=1`) and blocks them before they reach the server.
