# Structured Query Language (SQL) Injection Attacks

SQL is a commonly used language for querying relational databases (SQL databases).  These databases are used in a variety of applications, but are common as back-end data stores for many web applications.  SQL injection attacks are a common way of exploiting applications that do not properly sanitize user input.  Injection attacks work by submitting strings that can truncate or modify an SQL statement that uses variables defined by user-submitted data.

## Injection Techniques

### Credential Bypass by Truncation

For login fields that look up username and password data from a table, it might be possible to truncate the query string to return a user without submitting a password.

For example, an application that uses the following SQL query on a login page to return a singular user is vulnerable to truncation:

```php
$sql = "SELECT * FROM users WHERE username='$username' AND password='$password'";
```

This statement can return the same results by using the string `admin'#` effectively commenting out the password condition and turning the query string into:

```php
$sql = "SELECT * FROM users WHERE username='admin'#' AND password='$password'";
```
