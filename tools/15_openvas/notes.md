# OpenVAS: Theoretical Overview and Notes

## Introduction
OpenVAS (Open Vulnerability Assessment Scanner) is a full-featured vulnerability scanner. Its capabilities include unauthenticated testing, authenticated testing, various high-level and low-level Internet and industrial protocols, performance tuning for large-scale scans, and a powerful internal programming language to implement any type of vulnerability test. 
It is the scanner engine at the heart of the Greenbone Vulnerability Management (GVM) architecture.

## Core Architecture (GVM)
OpenVAS is rarely used in isolation; it is part of a larger ecosystem:
1.  **OpenVAS Scanner:** The actual scanning engine that executes Network Vulnerability Tests (NVTs).
2.  **Greenbone Vulnerability Manager (gvmd):** The central management service. It manages the database, schedules tasks, controls the scanner, and handles user management.
3.  **Greenbone Security Assistant (GSA):** The web-based graphical user interface that users interact with. It communicates with `gvmd` via the Greenbone Management Protocol (GMP).
4.  **PostgreSQL Database:** Stores configurations, scan results, and the feed data.

## Vulnerability Feeds
The scanner's effectiveness relies on its feeds, which must be updated regularly:
*   **NVT (Network Vulnerability Tests):** The scripts (written in NASL - Nessus Attack Scripting Language) that check for specific vulnerabilities.
*   **SCAP (Security Content Automation Protocol):** Data for compliance auditing and policy enforcement.
*   **CERT (Computer Emergency Response Team):** Advisories and information regarding known vulnerabilities.

## Scan Types
*   **Unauthenticated Scans:** The scanner acts like an external attacker, probing open ports, banner grabbing, and testing for known exploits against visible services. Prone to false positives and cannot see vulnerabilities inside the OS.
*   **Authenticated Scans (Credentialed Scans):** The scanner is provided with SSH or SMB credentials. It logs into the target machine, checks installed software versions, patch levels, and local configurations. This is significantly more accurate, produces fewer false positives, and is crucial for a comprehensive assessment.

## Best Practices
*   **Regular Updates:** Run `gvm-feed-update` frequently. A scanner is only as good as its latest signatures.
*   **Use Authenticated Scans:** Whenever possible, use credentials for internal scanning to get an accurate picture of the environment's security posture.
*   **Tune Scan Configurations:** Don't run "Full and very deep" scans on fragile legacy systems. Tailor the scan configuration to the target environment to avoid causing denial-of-service conditions.
*   **Triaging:** Vulnerability scanners generate noise. An ethical hacker's job is to manually verify the critical and high findings to confirm they are not false positives before including them in a report.
