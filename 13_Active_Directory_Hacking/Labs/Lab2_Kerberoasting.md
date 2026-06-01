# Lab 2: Kerberoasting Practice

## Goal: Steal and crack a service ticket.

## Steps:
1. **Request Tickets**: Use a tool like `GetUserSPNs.py` (from Impacket) to find service accounts and request their tickets.
   `python3 GetUserSPNs.py -dc-ip <DC_IP> domain.local/user:password`
2. **Save the Hash**: Save the output tickets to a file.
3. **Crack with Hashcat**:
   `hashcat -m 13100 hashes.txt /usr/share/wordlists/rockyou.txt`
4. **Log in**: Use the cracked password to access the service.

## Success Check:
- [ ] Successfully requested a service ticket.
- [ ] Cracked the ticket hash using a wordlist.
