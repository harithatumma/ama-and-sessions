# Joins, Aggregations, Normalization, and Indexes

# Database Setup

## Create students Table

```sql
CREATE TABLE students (
    student_id SERIAL PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(20)
);
```

---

## Create marks Table

```sql
CREATE TABLE marks (
    student_id INT,
    subject VARCHAR(30),
    score INT
);
```

---

## Insert Sample Data

```sql
INSERT INTO students(name, department)
VALUES
('Haritha', 'CSE'),
('Ravi', 'ECE'),
('Anu', 'CSE');
```

```sql
INSERT INTO marks(student_id, subject, score)
VALUES
(1, 'SQL', 90),
(2, 'Python', 75),
(1, 'DBMS', 85);
```

---

# 1. JOINS

JOIN combines data from multiple tables using related columns.

---

## INNER JOIN

Returns only matching rows from both tables.

```sql
SELECT students.name,
       marks.subject,
       marks.score
FROM students
INNER JOIN marks
ON students.student_id = marks.student_id;
```

---

## LEFT JOIN

Returns all rows from left table and matching rows from right table.

```sql
SELECT students.name,
       marks.subject
FROM students
LEFT JOIN marks
ON students.student_id = marks.student_id;
```

---

## RIGHT JOIN

Returns all rows from right table and matching rows from left table.

```sql
SELECT students.name,
       marks.subject
FROM students
RIGHT JOIN marks
ON students.student_id = marks.student_id;
```

---

## CROSS JOIN

Returns all possible combinations.

```sql
SELECT students.name,
       marks.subject
FROM students
CROSS JOIN marks;
```

---

## FULL OUTER JOIN

Returns combination of left join and right join.

```sql
SELECT students.name,
       marks.subject,
       marks.score
FROM students
FULL OUTER JOIN marks
ON students.student_id = marks.student_id;
```

---

## SELF JOIN

It is a join where a table is joined with itself to compare rows within the same table..

```sql
SELECT s1.name AS student_1,
       s2.name AS student_2,
       s1.department
FROM students s1
INNER JOIN students s2
ON s1.department = s2.department
AND s1.student_id <> s2.student_id;
```


# 2. AGGREGATIONS

Aggregation functions summarize multiple rows into one result.

---

## COUNT()

Counts rows.

```sql
SELECT COUNT(*)
FROM students;
```

---

## SUM()

Adds values.

```sql
SELECT SUM(score)
FROM marks;
```

---

## AVG()

Finds average value.

```sql
SELECT AVG(score)
FROM marks;
```

---

## MAX()

Finds highest value.

```sql
SELECT MAX(score)
FROM marks;
```

---

## MIN()

Finds lowest value.

```sql
SELECT MIN(score)
FROM marks;
```

---

## GROUP BY

Creates groups.

```sql
SELECT subject,
       AVG(score)
FROM marks
GROUP BY subject;
```

---

## HAVING

Filters grouped data.

```sql
SELECT subject,
       AVG(score)
FROM marks
GROUP BY subject
HAVING AVG(score) > 80;
```

---

# 3. NORMALIZATION

Normalization organizes tables to reduce duplicate data.

---

## Unnormalized Table

| student_name | subject | teacher |
| ------------ | ------- | ------- |
| Haritha      | SQL     | Ravi    |
| Haritha      | DBMS    | Ravi    |

Teacher name repeats.

---

## First Normal Form (1NF)

Each column should contain single values.

### Bad Example

| name    | subjects    |
| ------- | ----------- |
| Haritha | SQL, Python |

---

### Correct Example

| name    | subject |
| ------- | ------- |
| Haritha | SQL     |
| Haritha | Python  |

---

## Second Normal Form (2NF)

No partial dependency.

### Bad Example

| student_id | subject_id | student_name |
| ---------- | ---------- | ------------ |
| 1          | 101        | Haritha      |

student_name depends only on student_id.

---

### Correct Design

#### students

| student_id | student_name |
| ---------- | ------------ |
| 1          | Haritha      |

#### enrollments

| student_id | subject_id |
| ---------- | ---------- |
| 1          | 101        |

---

## Third Normal Form (3NF)

No transitive dependency.

### Bad Example

| emp_id | emp_name | dept_name |
| ------ | -------- | --------- |
| 1      | Haritha  | CSE       |

Department name repeats.

---

### Correct Design

#### employees

| emp_id | emp_name | dept_id |
| ------ | -------- | ------- |
| 1      | Haritha  | 10      |

#### departments

| dept_id | dept_name |
| ------- | --------- |
| 10      | CSE       |

---

## BCNF

Every determinant should be a candidate key.

### Example

| teacher | subject |
| ------- | ------- |
| Ravi    | SQL     |
| Ravi    | DBMS    |

If one teacher can teach multiple subjects and one subject can have multiple teachers,
then separate mapping tables are needed.

---

### Better Design

#### teachers

| teacher_id | teacher_name |
| ---------- | ------------ |
| 1          | Ravi         |

#### teacher_subjects

| teacher_id | subject |
| ---------- | ------- |
| 1          | SQL     |
| 1          | DBMS    |

---

# 4. INDEXES

Indexes improve search speed.

---

## Create Index

```sql
CREATE INDEX idx_student_name
ON students(name);
```

---

## Search Query

```sql
SELECT *
FROM students
WHERE name = 'Haritha';
```

---

## Drop Index

```sql
DROP INDEX idx_student_name;
```

---

## Types of Indexes

| Type              | Purpose                |
| ----------------- | ---------------------- |
| PRIMARY KEY Index | automatic unique index |
| UNIQUE Index      | prevents duplicates    |
| Composite Index   | multiple columns       |

