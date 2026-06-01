# Lab 1: Fixing SQLi (Conceptual)

## Goal: Understand how to write secure code.

## The Insecure Way (PHP):
`$query = "SELECT * FROM users WHERE username = '" . $_GET['user'] . "'";`
(User can put `' OR 1=1 --` here).

## The Secure Way (PHP):
`$stmt = $pdo->prepare('SELECT * FROM users WHERE username = :user');`
`$stmt->execute(['user' => $_GET['user']]);`

## Task:
1. Compare the two code snippets.
2. Notice how the second one uses a placeholder `:user` instead of adding the text directly.
3. Research "Parameterized Queries" on Google to see how they work in other languages (Python, Java).

## Success Check:
- [ ] I can identify "Insecure" vs "Secure" code.
- [ ] I understand why Prepared Statements stop SQLi.
