# Mini-Boss 3: The Logic Puzzle

## Goal: Bypass a complex API authorization.

## The Challenge:
An API has three endpoints:
1. `/login` (Returns a JWT token)
2. `/user/profile` (Requires JWT)
3. `/admin/config` (Requires Admin JWT)

You have a user account. You must find a way to modify your JWT token (or find a BOLA bug) to access the `/admin/config` endpoint without having the admin password.

## Success Criteria:
- [ ] Access the admin config page.
- [ ] Document whether you used a JWT attack (e.g., None algorithm) or a BOLA attack.
