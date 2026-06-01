# Burp Suite Examples

## Scenario: Bypassing Client-Side Validation

You are testing a web application's login portal. The application uses client-side JavaScript to ensure the password is at least 8 characters long before submitting the form. You want to test if the server-side validation is implemented.

### Setup and Execution

1. Configure your browser to proxy traffic through Burp Suite (usually `127.0.0.1:8080`).
2. In Burp Suite, go to **Proxy** -> **Intercept** and ensure "Intercept is on".
3. On the web app, enter a valid email and a password of 8 characters (e.g., `password`).
4. Click Login. The request will be captured in Burp Suite.
5. Modify the intercepted request to change the password to a 3-character string (e.g., `pwd`).
6. Click **Forward** to send the modified request to the server.

### Mocked HTTP Request (Intercepted)

```http
POST /api/login HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
Accept: application/json
Content-Type: application/json
Content-Length: 45

{"email": "admin@example.com", "password": "password"}
```

### Mocked HTTP Request (Modified)

```http
POST /api/login HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
Accept: application/json
Content-Type: application/json
Content-Length: 40

{"email": "admin@example.com", "password": "pwd"}
```

### Mocked HTTP Response

```http
HTTP/1.1 200 OK
Date: Fri, 31 May 2024 12:00:00 GMT
Content-Type: application/json
Content-Length: 28

{"status": "success", "token": "eyJhbG..."}
```

*Conclusion:* The server did not validate the password length, returning a successful login token.
