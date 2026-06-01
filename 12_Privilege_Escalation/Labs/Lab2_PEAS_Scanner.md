# Lab 2: Automated PrivEsc Scanning

## Goal: Use a tool to find privilege escalation paths.

## Tools to Use:
1. **LinPEAS (Linux Privilege Escalation Awesome Scripts)**: The best script for Linux. It highlights "very likely" root paths in red/yellow.
2. **WinPEAS**: The equivalent for Windows.

## The Flow:
1. **Transfer**: Upload the `.sh` or `.exe` file to the target machine.
2. **Run**: Execute the script.
3. **Analyze**: Scroll through the output and look for the colored highlights.

## Success Check:
- [ ] I can transfer a script to a target machine.
- [ ] I can run LinPEAS/WinPEAS and interpret the results.
