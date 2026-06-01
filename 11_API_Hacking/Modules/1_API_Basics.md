# Module 1: What is an API?

## Understanding APIs
An API (Application Programming Interface) is a way for two programs to talk to each other. Most modern websites and mobile apps are just "skins" that talk to an API in the background.

## REST APIs
The most common type of API. It uses standard HTTP methods:
- **GET**: Retrieve data (e.g., get user profile).
- **POST**: Send data (e.g., create a new post).
- **PUT**: Update data (e.g., change password).
- **DELETE**: Remove data (e.g., delete account).

## API Authentication
APIs don't usually use passwords; they use **Tokens** (like JWT - JSON Web Tokens). If you steal a token, you can impersonate the user without needing their password.
