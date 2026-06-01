# Responder - Notes

## Overview
Responder is a powerful network assessment tool created by Laurent Gaffié. It is designed to poison LLMNR, NBT-NS, and mDNS requests on a local network. When a machine on the network tries to resolve a hostname that DNS cannot find, Responder intercepts the request, claims to be the requested machine, and captures authentication hashes (usually NTLMv2) sent by the victim.

## How it Works
1. **Name Resolution Failure:** A user mistypes a share name (e.g., `\\filesrvr` instead of `\\fileserver`), or a script looks for a non-existent host.
2. **Fallback Protocols:** The Windows machine falls back to broadcast protocols like LLMNR (Link-Local Multicast Name Resolution) or NBT-NS (NetBIOS Name Service) to ask the local network, "Who is `filesrvr`?".
3. **Poisoning:** Responder, listening on the network, immediately replies, "I am `filesrvr`, my IP is [Attacker_IP]".
4. **Authentication:** The victim machine attempts to authenticate to the attacker's machine, sending its NTLMv2 hash.
5. **Capture/Relay:** Responder captures the hash, which can then be cracked offline (using Hashcat/John) or relayed to another machine using tools like `ntlmrelayx`.

## Mitigation
- **Disable LLMNR and NBT-NS:** This is the most effective defense. It can be done via Group Policy (GPO) and DHCP configurations.
- **Enable SMB Signing:** Prevents NTLM relay attacks (though it doesn't prevent hash capture).
- **Strong Passwords:** Ensures captured NTLMv2 hashes are difficult to crack offline.
