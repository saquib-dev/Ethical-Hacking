# Module 2: XXE (XML External Entity)

## What is XXE?
XXE occurs when an application parses XML input that contains a reference to an external entity.
Example: You send an XML file that tells the server: "Please go to `/etc/passwd` and include the content of that file in your response."

## Common Uses:
1. **File Read**: Reading sensitive files on the server.
2. **SSRF**: Using the XML parser to make requests to internal systems.
3. **Denial of Service**: "Billion Laughs" attack that crashes the server.
