# Module 08: Web Attacks I (SQL Injection)

## 1. What is SQL Injection (SQLi)?
SQL Injection is a vulnerability that allows an attacker to interfere with the queries that an application makes to its database. It happens when user input is directly inserted into a SQL query without being cleaned (sanitized).

### How it Works (The Logic)
**Normal Query**: `SELECT * FROM users WHERE username = 'admin' AND password = 'password123';`

**The Attack**: If the attacker enters `' OR 1=1 --` as the username.
**Modified Query**: `SELECT * FROM users WHERE username = '' OR 1=1 --' AND password = '...';`

**Why it works**:
- `1=1` is always **True**.
- `--` is a comment in SQL, which tells the database to ignore the rest of the query (the password check).
- The database sees a `True` statement and lets the attacker in.

## 2. Types of SQL Injection

### A. In-band SQLi (Classic)
The attacker uses the same communication channel to launch the attack and gather the results.
- **Error-based**: The database returns an error message that reveals table names or columns.
- **Union-based**: The attacker uses the `UNION` operator to combine the results of the original query with a custom query to steal data.

### B. Inferential SQLi (Blind)
The server does not return data or errors; it only returns "True" or "False" (e.g., the page loads normally or shows "User not found").
- **Boolean-based**: The attacker asks the DB a Yes/No question: `"Does the first letter of the admin password start with 'A'?"`
- **Time-based**: The attacker tells the DB to wait: `"If the admin password starts with 'A', wait 5 seconds."`

## 3. Prevention (The Right Way)
- **Prepared Statements (Parameterized Queries)**: The most effective defense. The SQL query is pre-compiled, and user input is treated as "data," not "code."
- **Input Validation**: Only allow expected characters (e.g., an age field should only allow numbers).
