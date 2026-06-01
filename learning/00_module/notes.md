# Module 00: Introduction to Ethical Hacking

## 1. What is Ethical Hacking?
Ethical hacking is the practice of legally breaking into computers and devices to test an organization's defenses. Unlike malicious hacking, ethical hacking is performed with **explicit permission**.

### The Three Hat Colors
*   **White Hat (Ethical Hacker)**: Hired by companies to find vulnerabilities. They follow a strict code of ethics and legal contracts.
*   **Black Hat (Cracker)**: Breaks into systems for personal gain, malice, or political reasons. Their actions are illegal.
*   **Grey Hat**: Operates in the middle. They might find a bug without permission but report it to the company instead of exploiting it. This is still technically illegal in many jurisdictions.

## 2. The Legal Framework
**Crucial Warning**: Hacking without written permission is a crime (e.g., the Computer Misuse Act in the UK or the CFAA in the USA), regardless of your intent.

### Essential Documents
*   **Permission/Authorization**: A signed document giving you the right to test.
*   **Scope of Work (SOW)**: Defines exactly *what* is being tested (which IPs, which domains) and what is *off-limits*.
*   **Rules of Engagement (ROE)**: Defines *how* the test is performed (e.g., "No Denial of Service attacks," "Only test between 2 AM and 5 AM").

## 3. The Ethical Hacking Process
Penetration testing typically follows these five phases:
1.  **Reconnaissance**: Gathering information about the target.
2.  **Scanning & Enumeration**: Identifying open ports and services.
3.  **Gaining Access (Exploitation)**: Using vulnerabilities to enter the system.
4.  **Maintaining Access**: Ensuring you can get back in (persistence).
5.  **Covering Tracks/Reporting**: Cleaning up and documenting everything.

## 4. The Hacking Mindset
*   **Critical Thinking**: Don't just run tools; ask "If I were the developer, where would I have made a mistake?"
*   **Persistence**: If one way fails, try ten more.
*   **Attention to Detail**: A single misplaced character in a payload can be the difference between failure and success.
