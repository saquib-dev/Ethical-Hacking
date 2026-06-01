# Lab 1: Creating a Phishing Page (Conceptual)

## Goal: Understand how phishing pages are built.

## Tool: Social Engineering Toolkit (SET)
SET is the industry standard for social engineering on Kali Linux.

## The Flow:
1. **Launch SET**: `sudo setoolkit`
2. **Select Social-Engineering Attacks** $\rightarrow$ **Website Attack Vectors** $\rightarrow$ **Credential Harvester Attack Method**.
3. **Clone Website**: SET asks you for a URL (e.g., `facebook.com`). It creates an exact copy of that page on your machine.
4. **Capture**: When a user enters their email and password on your fake page, SET displays them in your terminal.

## Success Check:
- [ ] I understand how SET clones a website.
- [ ] I understand how "Credential Harvesting" works.
