# Module 07: Web Fundamentals Lab

### Task 1: Header Analysis
1. Use `curl -I` on three different websites.
2. Identify the `Server` header (e.g., `Server: nginx/1.18.0`).
3. Look for the `X-Powered-By` header. Which language is the site using (PHP, ASP.NET)?

### Task 2: Intercepting Traffic with Burp Suite
1. Install **Burp Suite Community Edition**.
2. Configure your browser proxy (using **FoxyProxy** extension is recommended).
3. Go to a test site, turn "Intercept ON" in Burp, and submit a form.
4. Modify the data in the request (e.g., change `username=user` to `username=admin`) and forward it.

### Task 3: Exploring the DOM
1. Open any website and press **F12** to open DevTools.
2. Go to the **Elements** tab. Find a button or text and change it. (Notice that this only changes on your screen, not the server).
3. Go to the **Console** tab and type `alert('Hacked!')`. This is the first step to learning XSS.
