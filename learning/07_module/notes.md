# Module 07: Web Application Fundamentals

## 1. The Web Architecture
To hack a website, you must understand how the "Conversation" between a browser and a server works.

### The Request-Response Cycle
1. **Request**: Your browser (Client) asks for a page.
2. **Processing**: The server (Apache, Nginx) processes the request, maybe talks to a Database (MySQL, PostgreSQL).
3. **Response**: The server sends back the page (HTML, CSS, JS).

## 2. HTTP Protocol Deep Dive
HTTP is a "stateless" protocol, meaning the server forgets who you are the moment the request is over. To solve this, we use **Cookies** and **Sessions**.

### HTTP Methods
- **GET**: "Give me this data." (Data is visible in the URL).
- **POST**: "Here is some data to process." (Data is hidden in the request body).
- **PUT**: "Update this existing data."
- **DELETE**: "Remove this data."

### HTTP Status Codes
| Code | Meaning | Hacker's Interpretation |
| :--- | :--- | :--- |
| **200** | OK | Success! The page/resource exists. |
| **301/302** | Redirect | The page moved. Check where it's redirecting to. |
| **401/403** | Unauthorized | You found a restricted area! Now, how do you bypass it? |
| **404** | Not Found | Page doesn't exist. Great for "Fuzzing" (guessing names). |
| **500** | Server Error | The server crashed. This often reveals a bug you can exploit. |

## 3. Client-Side vs. Server-Side
- **Client-Side**: HTML, CSS, JavaScript. This runs in **your** browser. You can see and modify it.
- **Server-Side**: PHP, Python, Java, Node.js. This runs on **the server**. You can never see this code unless you find a leak.
