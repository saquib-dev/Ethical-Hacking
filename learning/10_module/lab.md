# Lab: Exploiting LFI and IDOR

## Goal
Identify and exploit an Insecure Direct Object Reference (IDOR) to access another user's data, and exploit a Local File Inclusion (LFI) vulnerability to read system files.

## Scenario
You are testing a web application that has a user profile page and a document viewer feature.

## Phase 1: IDOR Exploitation
1. **Log in** to the application as a standard user.
2. **Navigate** to your profile page. Notice the URL: `http://target.local/profile.php?user_id=105`.
3. **Modify the ID:** Change the `user_id` parameter to `100` (which is likely the admin or first user).
4. **Result:** If you can see the admin's profile details (like email or API keys) without being logged in as the admin, you have successfully exploited an IDOR.

## Phase 2: LFI Exploitation
1. **Navigate** to the document viewer. Notice the URL: `http://target.local/view.php?file=report.pdf`.
2. **Test for LFI:** Replace `report.pdf` with directory traversal payloads to attempt to read the `/etc/passwd` file.
   - Try: `?file=../../../../etc/passwd`
3. **Bypass Filters:** If the application appends `.pdf` to your input, try a null byte (if applicable): `?file=../../../../etc/passwd%00`.
4. **Extract Source Code:** Use the PHP filter wrapper to read the source code of the database connection file (e.g., `db.php`).
   - Try: `?file=php://filter/convert.base64-encode/resource=db.php`
5. **Result:** Decode the base64 string to reveal the database credentials.

## Success Check:
- [ ] Successfully accessed another user's profile via IDOR.
- [ ] Successfully read the `/etc/passwd` file via LFI.
- [ ] Successfully extracted the database credentials using PHP wrappers.
