# Lab 2: Simple Port Scanner in Python

## Goal: Build your own basic Nmap from scratch.

## Task:
Using the `socket` library in Python, write a script that:
1. Takes an IP address and a range of ports.
2. Attempts to connect to each port.
3. Prints "Port Open" if the connection is successful.

## Concept to Learn:
Understand the **TCP Three-Way Handshake** (SYN $\rightarrow$ SYN-ACK $\rightarrow$ ACK). Your script is essentially performing the first two steps.

## Success Check:
- [ ] Script correctly identifies open ports on your own VM.
- [ ] You understand the difference between a "closed" and "filtered" port.
