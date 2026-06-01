# Netcat Examples

## Scenario: Testing Network Connectivity and Firewall Rules
Netcat can be used to set up a temporary listening service to verify if a specific port is reachable through a firewall from another machine.

**Command (Listener on Server):**
```bash
nc -lvnp 8080
```

**Command (Client testing connection):**
```bash
nc -vz 10.10.10.5 8080
```

**Mocked Output (Client):**
```text
Connection to 10.10.10.5 8080 port [tcp/*] succeeded!
```

**Mocked Output (Listener):**
```text
listening on [any] 8080 ...
connect to [10.10.10.5] from (UNKNOWN) [10.10.10.100] 53214
```

**Explanation:**
- `-l`: Listen mode, used to wait for incoming connections.
- `-v`: Verbose output, providing more details about the connection status.
- `-n`: Do not resolve DNS (avoids reverse DNS lookups, speeding up the connection).
- `-p 8080`: Specify the local port to listen on.
- `-z`: Zero-I/O mode. Used on the client side to scan or test if a port is open without sending any data.
