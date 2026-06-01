# OpenVAS / Greenbone Vulnerability Management Cheat Sheet

*Note: OpenVAS is now heavily integrated into the Greenbone Community Edition (GCE) architecture. Most interaction is done via the Web UI (Greenbone Security Assistant - GSA) or the `gvm-cli` tool.*

## Service Management (Kali Linux/Debian based)
*   **Initial Setup (Downloads feeds, sets up DB):** `sudo gvm-setup`
*   **Check Setup Status:** `sudo gvm-check-setup`
*   **Start GVM Services:** `sudo gvm-start`
*   **Stop GVM Services:** `sudo gvm-stop`
*   **Update Feeds (NVTs, SCAP, CERT):** `sudo gvm-feed-update`

## Administrative Commands
*   **Change Admin Password:** `sudo runuser -u _gvm -- gvmd --user=admin --new-password=<new_password>`
*   **Check Scanner Status:** `sudo runuser -u _gvm -- gvmd --get-scanners`

## Command Line Interface (gvm-cli)
*Requires `gvm-tools` package.*

*   **Connect via Unix Socket (Local):** `gvm-cli socket --xml "<get_version/>"`
*   **Connect via TLS (Remote):** `gvm-cli tls --hostname <IP> --xml "<get_version/>"`
*   **List Users:** `gvm-cli socket --xml "<get_users/>"`
*   **List Tasks:** `gvm-cli socket --xml "<get_tasks/>"`
*   **Start a Task:** `gvm-cli socket --xml "<start_task task_id='<UUID>'/>"`

## Web Interface (Greenbone Security Assistant)
*   **Default URL:** `https://127.0.0.1:9392`
*   **Default User:** `admin` (password set during `gvm-setup`)

## Important Log Files
*   **Scanner Logs:** `/var/log/gvm/openvas.log`
*   **Manager Logs:** `/var/log/gvm/gvmd.log`
*   **Web UI Logs:** `/var/log/gvm/gsad.log`
