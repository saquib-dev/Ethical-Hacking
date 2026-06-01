# Lab 1: Intercepting API Traffic

## Goal: See how your browser talks to an API.

## Tool: Burp Suite (The essential tool for all web/API hacking).

## Steps:
1. **Start Burp Suite** (Pre-installed on Kali).
2. **Use the Built-in Browser**: Open the Burp browser.
3. **Visit a Site**: Go to any modern site (like a weather app or social site).
4. **Inspect Proxy**: Look at the "HTTP history" tab.
5. **Find the API**: Look for requests that go to `/api/v1/...` or return JSON data (looks like `{ "key": "value" }`).

## Success Check:
- [ ] Successfully intercepted an API request.
- [ ] Identified the HTTP method (GET, POST, etc.) being used.
- [ ] Read the JSON response from the server.
