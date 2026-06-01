# Practical Lab: Vulnerability Scanning with OpenVAS

## Scenario
You are tasked with performing an internal vulnerability assessment for a small network segment. You need to configure OpenVAS to scan a target subnet, identify potential vulnerabilities, and generate a report for the IT team.

## Objectives
1.  Ensure OpenVAS services are running and feeds are up to date.
2.  Create a target definition for the scan.
3.  Configure and launch a vulnerability scanning task.
4.  Review the scan results and generate a PDF report.

## Lab Environment
*   **Scanner:** Kali Linux with OpenVAS/GVM installed (Local IP: 10.0.0.10)
*   **Target:** Metasploitable 2 or a vulnerable Windows VM (IP: 10.0.0.50)

## Walkthrough

### Phase 1: Preparation
1.  Open a terminal on Kali Linux.
2.  Start the services: `sudo gvm-start`
3.  Open a web browser and navigate to `https://127.0.0.1:9392`.
4.  Log in using your administrative credentials.

### Phase 2: Configuration
1.  **Create a Target:**
    *   Navigate to **Configuration** -> **Targets**.
    *   Click the New Target icon (star).
    *   Name: `Internal Web Server`
    *   Hosts: `10.0.0.50`
    *   Port List: Leave as default (All IANA assigned TCP).
    *   Click **Save**.
2.  **Create a Task:**
    *   Navigate to **Scans** -> **Tasks**.
    *   Click the New Task icon (star) -> **New Task**.
    *   Name: `Initial Assessment - Web Server`
    *   Scan Targets: Select `Internal Web Server`.
    *   Scanner: OpenVAS Default.
    *   Scan Config: Select `Full and fast` (a good balance of speed and coverage).
    *   Click **Save**.

### Phase 3: Execution and Analysis
1.  **Run the Scan:**
    *   In the Tasks view, find your new task and click the Play icon (Start) under the Actions column.
    *   Wait for the status to change from Requested -> Running -> Done. This may take several minutes.
2.  **Review Results:**
    *   Once the task is Done, click on the number in the **Reports** column.
    *   Click on the Date of the report to view the details.
    *   Review the vulnerabilities found, sorted by severity (High, Medium, Low).
    *   Click on a specific vulnerability (e.g., "SSH Weak Algorithms Supported") to read the description, impact, and mitigation advice.
3.  **Generate Report:**
    *   In the report view, click the Download icon.
    *   Select **PDF** as the format and click **OK**.
    *   Review the generated document.
