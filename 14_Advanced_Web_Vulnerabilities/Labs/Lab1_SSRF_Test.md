# Lab 1: Testing for SSRF

## Goal: Use a "Fetch" feature to read internal data.

## Practice:
Use a dedicated lab like PortSwigger Web Security Academy.

## Steps:
1. Find a parameter that takes a URL (e.g., `?url=http://google.com`).
2. Change it to `?url=http://localhost:80`.
3. Try to access internal admin panels: `?url=http://localhost/admin`.
4. If on Cloud, try: `?url=http://169.254.169.254/latest/meta-data/`.

## Success Check:
- [ ] Successfully made the server request an internal URL.
- [ ] Captured data that is not available to the public.
