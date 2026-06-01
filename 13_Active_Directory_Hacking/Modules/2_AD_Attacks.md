# Module 2: AD Attack Techniques

## Kerberos and Tickets
AD uses a system called **Kerberos** for authentication. Instead of passwords, users get "Tickets" to access services.
- **Kerberoasting**: Stealing a service ticket and cracking it offline to get the service account password.
- **AS-REP Roasting**: Attacking users who don't require "pre-authentication" to get their password hashes.

## Lateral Movement in AD
- **Pass-the-Hash (PtH)**: Using a stolen password hash to log in without knowing the actual password.
- **Pass-the-Ticket (PtT)**: Stealing a Kerberos ticket to impersonate a user.

## Domain Dominance
The goal is to become a **Domain Admin**. Once you are, you can control everything.
