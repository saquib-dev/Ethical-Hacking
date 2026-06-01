# Module 1: What is C2?

## Command & Control (C2)
C2 is the infrastructure used by a hacker to maintain communication with compromised systems (beacons) over a long period.

## How C2 Differs from a Reverse Shell:
- **Reverse Shell**: One-to-one, fragile, easily detected. If the connection drops, you are out.
- **C2 Framework**: One-to-Many. The compromised machine "beacons" (checks in) every few minutes. You queue commands, and the machine executes them the next time it checks in.

## The Architecture:
`Beacons (Victims)` $\rightarrow$ `Redirectors (Proxies)` $\rightarrow$ `C2 Server (Attacker)`.
Redirectors are used so that if the security team finds the IP, they find a proxy, not the actual attacker's server.
