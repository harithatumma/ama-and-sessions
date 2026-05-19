# Technical Paper: SQL, PostgreSQL, and Python Interview Questions & Answers

---

# 1. What is CROSS JOIN?

## Definition

A CROSS JOIN returns all possible combinations of rows from two tables.

---

## Formula

Rows in Table1 × Rows in Table2

---

## Example

### colors

| color |
| ----- |
| Red   |
| Blue  |

### sizes

| size |
| ---- |
| S    |
| M    |

---

## Query

```sql
SELECT *
FROM colors
CROSS JOIN sizes;
```

---

## Result

| color | size |
| ----- | ---- |
| Red   | S    |
| Red   | M    |
| Blue  | S    |
| Blue  | M    |

---

## Use Cases

* generating combinations
* testing
* product variations

---

# 2. What is PostgreSQL?

PostgreSQL is an open-source relational database management system (RDBMS).

---

## Features

* stores structured data
* supports SQL
* ACID compliant
* supports transactions
* highly scalable

---

## Used In

* web applications
* banking systems
* analytics
* backend systems

---

# 3. What is a Transaction?

A transaction is a group of SQL operations executed as a single unit.

---

## Example

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 1000
WHERE id = 1;

UPDATE accounts
SET balance = balance + 1000
WHERE id = 2;

COMMIT;
```

---

## Important Commands

| Command  | Purpose           |
| -------- | ----------------- |
| BEGIN    | Start transaction |
| COMMIT   | Save permanently  |
| ROLLBACK | Undo changes      |

---

# 4. Use of SAVEPOINT()

SAVEPOINT creates a checkpoint inside a transaction.

Instead of rolling back the entire transaction,
we can rollback to a specific point.

---

## Example

```sql
BEGIN;

UPDATE accounts
SET balance = balance - 500
WHERE id = 1;

SAVEPOINT sp1;

UPDATE accounts
SET balance = balance + 500
WHERE id = 2;

ROLLBACK TO sp1;

COMMIT;
```

---

## What Happens?

* First update remains
* Second update is undone

---

# 5. Difference Between LEFT JOIN and INNER JOIN

| Feature                        | INNER JOIN     | LEFT JOIN             |
| ------------------------------ | -------------- | --------------------- |
| Returns matching rows          | Yes            | Yes                   |
| Returns non-matching left rows | No             | Yes                   |
| NULL values possible           | No             | Yes                   |
| Most used for                  | common records | keeping all left data |

---

## Example

### INNER JOIN

Returns only matching records.

### LEFT JOIN

Returns:

* all rows from left table
* matching rows from right table

---

# 6. How Can We Achieve Polymorphism in Python?

Polymorphism means:

same method behaves differently for different objects

---

## Example

```python
class Dog:
    def sound(self):
        print("Bark")

class Cat:
    def sound(self):
        print("Meow")

animals = [Dog(), Cat()]

for a in animals:
    a.sound()
```

---

## Output

```text
Bark
Meow
```

---

## Types

* Method Overriding
* Duck Typing
* Operator Overloading

---

# 7. Difference Between JOIN and INNER JOIN

There is practically NO difference.

---

## Why?

In SQL:

```sql
JOIN
```

by default means:

```sql
INNER JOIN
```

---

## Example

Both queries are same:

```sql
SELECT *
FROM students
JOIN marks
ON students.id = marks.id;
```

```sql
SELECT *
FROM students
INNER JOIN marks
ON students.id = marks.id;
```

---

# 8. What is Atomicity in ACID?

Atomicity means:

either all operations happen or none happen

---

## Example

Bank transfer:

1. deduct money
2. add money

If second step fails,
first step is also undone.

---

## Related Command

```sql
ROLLBACK;
```

used to undo transaction.

---

# 9. How to Connect to PostgreSQL by Terminal

## Command

```bash
psql -U username -d database_name
```

---

## Example

```bash
psql -U postgres -d testdb
```

---

## With Host

```bash
psql -h localhost -U postgres -d testdb
```

---

## Meaning

| Option | Meaning  |
| ------ | -------- |
| -U     | Username |
| -d     | Database |
| -h     | Host     |

---

# 10. What are Subqueries?

A subquery is a query inside another query.

---

## Example

```sql
SELECT name
FROM employees
WHERE salary >
(
    SELECT AVG(salary)
    FROM employees
);
```

---

## How It Works

Inner query:

```sql
SELECT AVG(salary)
FROM employees;
```

returns average salary.

Outer query finds employees earning above average.

---

# 11. What are File Pointer Methods in Python?

File pointer controls current reading/writing position in a file.

---

## Important Methods

| Method | Purpose          |
| ------ | ---------------- |
| tell() | current position |
| seek() | move pointer     |
| read() | read data        |

---

## Example

```python
f = open("demo.txt", "r")

print(f.tell())

f.seek(5)

print(f.tell())
```

---

# 12. Difference Between PRIMARY KEY and UNIQUE Constraint

| Feature         | PRIMARY KEY     | UNIQUE                 |
| --------------- | --------------- | ---------------------- |
| Uniqueness      | Yes             | Yes                    |
| NULL allowed    | No              | Yes (usually one NULL) |
| Count per table | One             | Multiple               |
| Purpose         | Main identifier | Prevent duplicates     |

---

## Example

```sql
CREATE TABLE students(
    id INT PRIMARY KEY,
    email VARCHAR(50) UNIQUE
);
```

---

# 13. What is De-normalization?

Denormalization means:

adding redundant data intentionally

to improve query performance.

---

## Why Used?

Normalization reduces redundancy but increases joins.

Too many joins may slow queries.

Denormalization reduces joins for faster reads.

---

## Example

Instead of separate:

* customers table
* orders table

some customer data may be copied into orders table.

---

# 14. What is ROLLUP?

ROLLUP is used with GROUP BY to create subtotals and grand totals.

---

## Example

```sql
SELECT department,
       SUM(salary)
FROM employees
GROUP BY ROLLUP(department);
```

---

## Result

| department | sum    |
| ---------- | ------ |
| IT         | 100000 |
| HR         | 80000  |
| NULL       | 180000 |

---

## NULL Row Means

Grand total.

---

# 15. Difference Between OFFSET and LIMIT

| Feature      | LIMIT                   | OFFSET         |
| ------------ | ----------------------- | -------------- |
| Purpose      | restrict number of rows | skip rows      |
| Used for     | pagination              | pagination     |
| Returns rows | specified count         | after skipping |

---

## Example

```sql
SELECT *
FROM employees
LIMIT 5;
```

Returns first 5 rows.

---

## OFFSET Example

```sql
SELECT *
FROM employees
LIMIT 5 OFFSET 10;
```

---

## Meaning

skip first 10 rows
then return next 5 rows

---
