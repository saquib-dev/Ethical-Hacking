# Lab 2: Using a Redirector (Conceptual)

## Goal: Understand how to hide the C2 server.

## The Setup:
`Windows Target` $\rightarrow$ `VPS (Redirector)` $\rightarrow$ `Kali (C2 Server)`

## How it works:
1. You set up a simple VPS (Virtual Private Server).
2. You install a tool like **Socat** or **Nginx** on the VPS.
3. All traffic sent to the VPS is automatically forwarded to your Kali machine.
4. If the target's security team blocks the IP, they only block the VPS, and your main server remains safe.

## Success Check:
- [ ] I understand the role of a redirector in professional operations.
- [ ] I can explain why direct C2 connections are a risk.
