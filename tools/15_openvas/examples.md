# OpenVAS (Greenbone) Examples

## Scenario: Initiating a Vulnerability Scan via CLI
While OpenVAS is typically operated via its web interface (Greenbone Security Assistant - GSA), the `gvm-cli` tool allows administrators to automate vulnerability scanning and integrate it into CI/CD pipelines or reporting scripts.

**Command:**
```bash
gvm-cli socket --xml "<create_task><name>Weekly Subnet Scan</name><config id='daba56c8-73ec-11df-a475-002264764cea'/><target id='12345abc'/></create_task>"
```

**Mocked Output:**
```xml
<create_task_response status="201" status_text="OK">
  <task id="9876xyz-task-id-1234" />
</create_task_response>
```

**Explanation:**
- `gvm-cli socket`: Connects to the local Greenbone daemon via a Unix socket.
- `--xml "..."`: Sends a raw XML command (GMP/OMP protocol) to the scanner.
- `<config id='...'>`: The UUID corresponding to the desired scan configuration (e.g., "Full and fast").
- `<target id='...'>`: The UUID of the previously configured target network or host group.
