# Module 3: Unrestricted File Upload

## What is it?
When a website lets you upload a file but doesn't check what *kind* of file it is.

## The Goal: Remote Code Execution (RCE)
If you can upload a `.php`, `.jsp`, or `.asp` file, you can upload a **Web Shell**. Once uploaded, you just visit the URL of the file, and you can run commands on the server.

## Bypassing Filters:
- **Extension Bypass**: Try `.php5`, `.phtml`, or `.php.jpg`.
- **MIME-type Bypass**: Change `Content-Type` to `image/jpeg` in Burp Suite.
- **Magic Bytes Bypass**: Add the first few bytes of a real JPEG to the start of your shell.
