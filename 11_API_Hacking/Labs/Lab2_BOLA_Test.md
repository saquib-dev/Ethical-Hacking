# Lab 2: Testing for BOLA (Conceptual)

## Goal: Try to access another user's data via an API.

## Task:
Imagine you found an API endpoint: `https://api.example.com/v1/profile?id=500`

1. **Analyze**: Notice that the `id` is a simple number.
2. **Test**: Change the `id` to `501`, `502`, `499`.
3. **Observe**: If the server returns data for people who are not you, you found a **BOLA** vulnerability.

## Success Check:
- [ ] Understand how to manipulate API parameters to find BOLA.
- [ ] Know how to use Burp Suite "Repeater" to quickly test different IDs.
