# Module 2: Common API Flaws

## BOLA (Broken Object Level Authorization)
The most common API bug. It's like IDOR for APIs.
Example: You are logged in as User A. You request `/api/users/100`. You then change it to `/api/users/101` and the API gives you User B's private data.

## Mass Assignment
The API lets you update fields you shouldn't.
Example: You update your profile via `/api/update` with `{"name": "Bob"}`. You try adding `{"is_admin": true}` and the API actually makes you an admin.

## Excessive Data Exposure
The API returns way more data than the frontend actually shows.
Example: The website only shows your username, but the API response includes your home address and phone number.
