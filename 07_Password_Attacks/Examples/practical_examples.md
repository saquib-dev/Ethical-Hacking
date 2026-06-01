# Module 07 Examples: Web Application Fundamentals

## 1. Raw HTTP GET Request and Response
When you visit `http://example.com`, your browser sends a raw text request like this:

**The Request (Client $\rightarrow$ Server):**
```http
GET / HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)
Accept: text/html,application/xhtml+xml
Cookie: session_id=xyz123abc
Connection: close
```

**The Response (Server $\rightarrow$ Client):**
```http
HTTP/1.1 200 OK
Date: Mon, 25 Jul 2026 12:00:00 GMT
Server: Apache/2.4.41 (Ubuntu)
Content-Type: text/html; charset=UTF-8

<!DOCTYPE html>
<html>
<head><title>Welcome</title></head>
<body><h1>Hello World!</h1></body>
</html>
```

## 2. Analyzing a POST Request (Login Form)
When you submit a login form, the data is typically sent via a POST request.

**The Request:**
```http
POST /login.php HTTP/1.1
Host: targetsite.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 38

username=admin&password=SuperSecret123!
```

## 3. Directory Brute-Forcing (Fuzzing) Example
Using `gobuster` to find hidden files and directories (looking for 200 OK, ignoring 404 Not Found):
```bash
gobuster dir -u http://targetsite.com/ -w /usr/share/wordlists/dirb/common.txt
```
