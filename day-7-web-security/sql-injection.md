# SQL Injection Lab

## Lab
SQL injection vulnerability in WHERE clause allowing retrieval of hidden data

## Objective
Test whether the `category` parameter is vulnerable to SQL injection and determine whether hidden products can be retrieved.

## Normal Request
```text
GET /filter?category=Gifts
## First Test
The category value was changed to:

Gifts'

The application returned:

500 Internal Server Error

## Exploitation Test
The parameter was changed to:

Gifts' OR 1=1--

The application returned the page and the lab reported Solved.

## Vulnerable Behavior
The category input was incorporated into a backend SQL query without being safely separated from SQL syntax.

## Impact
An attacker could potentially manipulate the application's database query to retrieve data outside the intended category.

## Prevention
Use parameterized queries or prepared statements so user input is treated as data rather than SQL syntax. Apply least-privilege permissions to the database account and avoid exposing unnecessary database errors.

