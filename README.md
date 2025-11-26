# Oracle SQL & PL/SQL Complete Training Guide

## 📚 Table of Contents

### SQL Fundamentals
1. Introduction to Oracle & RDBMS
2. SQL Commands Overview
3. Data Types
4. Tables & Records
5. SQL Operators
6. Clauses & Conditions
7. Joins
8. Sub Queries
9. Built-in Functions
10. Constraints
11. Database Objects

### PL/SQL Programming
12. PL/SQL Basics
13. Control Structures
14. Cursors
15. Exception Handling
16. Collections
17. Stored Procedures & Functions
18. Packages16. [Collections](#collections)
19. Triggers
17. [Stored Procedures & Functions](#stored-procedures--functions)
18. [Packages](#packages)
19. [Triggers](#triggers)

---

## Introduction to Oracle & RDBMS

### What is Oracle?
- Oracle is a **Relational Database Management System (RDBMS)**
- Industry-leading enterprise database solution
- Supports large-scale data management and processing

### RDBMS Concepts
- **Database**: Collection of related tables
- **Table**: Collection of records organized in rows and columns
- **Record/Row**: Single entry in a table
- **Field/Column**: Specific attribute in a table

### Key Features
- Data integrity and consistency
- Multi-user support
- Security and access control
- Transaction management
- Backup and recovery

---

## SQL Commands Overview

### DDL - Data Definition Language
**Purpose**: Define and modify database structure

```sql
CREATE   -- Create new database objects
ALTER    -- Modify existing objects
DROP     -- Delete objects
TRUNCATE -- Remove all records from table
RENAME   -- Rename objects
```

### DRL/DQL - Data Retrieval/Query Language
**Purpose**: Retrieve data from database

```sql
SELECT   -- Query and retrieve data
```

### DML - Data Manipulation Language
**Purpose**: Manipulate data in tables

```sql
INSERT   -- Add new records
UPDATE   -- Modify existing records
DELETE   -- Remove records
```

### TCL - Transaction Control Language
**Purpose**: Manage database transactions

```sql
COMMIT      -- Save changes permanently
ROLLBACK    -- Undo changes
SAVEPOINT   -- Create transaction savepoint
```

### DCL - Data Control Language
**Purpose**: Control access to database

```sql
GRANT    -- Give privileges
REVOKE   -- Remove privileges
```

---

## Data Types

### Character Data Types
| Data Type | Description | Max Size |
|-----------|-------------|----------|
| CHAR(size) | Fixed-length character | 2000 bytes |
| VARCHAR2(size) | Variable-length character | 4000 bytes |
| LONG | Variable-length character | 2 GB |

### Numeric Data Types
| Data Type | Description |
|-----------|-------------|
| NUMBER(p,s) | Fixed and floating-point numbers |
| INTEGER | Whole numbers |
| FLOAT | Floating-point numbers |

### Date & Time Data Types
| Data Type | Description |
|-----------|-------------|
| DATE | Date and time |
| TIMESTAMP | Date and time with fractional seconds |

### Large Object Data Types
| Data Type | Description | Max Size |
|-----------|-------------|----------|
| CLOB | Character Large Object | 4 GB |
| BLOB | Binary Large Object | 4 GB |

---

## Tables & Records

### Creating Tables

```sql
CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    ...
);

-- Example
CREATE TABLE employees (
    emp_id NUMBER(5) PRIMARY KEY,
    emp_name VARCHAR2(50) NOT NULL,
    salary NUMBER(10,2),
    hire_date DATE DEFAULT SYSDATE
);
```

### Inserting Records

```sql
-- Insert all columns
INSERT INTO table_name VALUES (value1, value2, ...);

-- Insert specific columns
INSERT INTO table_name (column1, column2) VALUES (value1, value2);

-- Insert multiple records
INSERT ALL
    INTO table_name VALUES (value1, value2)
    INTO table_name VALUES (value3, value4)
SELECT * FROM dual;
```

### Updating Records

```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```

### Deleting Records

```sql
DELETE FROM table_name WHERE condition;
```

### Modifying Tables

```sql
-- Add column
ALTER TABLE table_name ADD column_name datatype;

-- Modify column
ALTER TABLE table_name MODIFY column_name new_datatype;

-- Drop column
ALTER TABLE table_name DROP COLUMN column_name;

-- Rename column
ALTER TABLE table_name RENAME COLUMN old_name TO new_name;
```

---

## SQL Operators

### Arithmetic Operators
```sql
+  (Addition)
-  (Subtraction)
*  (Multiplication)
/  (Division)
```

### Comparison Operators
```sql
=   (Equal to)
!=  (Not equal to)
>   (Greater than)
<   (Less than)
>=  (Greater than or equal to)
<=  (Less than or equal to)
```

### Logical Operators
```sql
AND  -- All conditions must be true
OR   -- At least one condition must be true
NOT  -- Negates a condition
```

### Special Operators
```sql
BETWEEN ... AND ...  -- Range check
IN (list)            -- Match any value in list
LIKE                 -- Pattern matching
IS NULL              -- Check for NULL values
```

---

## Clauses & Conditions

### WHERE Clause
```sql
SELECT * FROM table_name WHERE condition;
```

### ORDER BY Clause
```sql
SELECT * FROM table_name ORDER BY column_name [ASC|DESC];
```

### GROUP BY Clause
```sql
SELECT column1, COUNT(*)
FROM table_name
GROUP BY column1;
```

### HAVING Clause
```sql
SELECT column1, COUNT(*)
FROM table_name
GROUP BY column1
HAVING COUNT(*) > 5;
```

### DISTINCT Keyword
```sql
SELECT DISTINCT column_name FROM table_name;
```

---

## Joins

### Types of Joins

#### 1. INNER JOIN (EQUI JOIN)
```sql
SELECT columns
FROM table1
INNER JOIN table2 ON table1.column = table2.column;
```

#### 2. LEFT OUTER JOIN
```sql
SELECT columns
FROM table1
LEFT JOIN table2 ON table1.column = table2.column;
```

#### 3. RIGHT OUTER JOIN
```sql
SELECT columns
FROM table1
RIGHT JOIN table2 ON table1.column = table2.column;
```

#### 4. FULL OUTER JOIN
```sql
SELECT columns
FROM table1
FULL JOIN table2 ON table1.column = table2.column;
```

#### 5. SELF JOIN
```sql
SELECT a.column, b.column
FROM table1 a, table1 b
WHERE a.column = b.column;
```

#### 6. CROSS JOIN
```sql
SELECT * FROM table1 CROSS JOIN table2;
```

---

## Sub Queries

### Single Row Sub Query
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

### Multi Row Sub Query
```sql
SELECT * FROM employees
WHERE dept_id IN (SELECT dept_id FROM departments WHERE location = 'New York');
```

### Correlated Sub Query
```sql
SELECT e1.emp_name, e1.salary
FROM employees e1
WHERE salary > (SELECT AVG(salary) FROM employees e2 WHERE e1.dept_id = e2.dept_id);
```

---

## Built-in Functions

### String Functions

| Function | Description | Example |
|----------|-------------|--------|
| UPPER(string) | Converts to uppercase | UPPER('hello') → 'HELLO' |
| LOWER(string) | Converts to lowercase | LOWER('HELLO') → 'hello' |
| INITCAP(string) | Capitalizes first letter | INITCAP('hello world') → 'Hello World' |
| LENGTH(string) | Returns string length | LENGTH('Oracle') → 6 |
| SUBSTR(string, start, length) | Extracts substring | SUBSTR('Oracle', 1, 3) → 'Ora' |
| CONCAT(str1, str2) | Concatenates strings | CONCAT('Hello', 'World') → 'HelloWorld' |
| TRIM(string) | Removes leading/trailing spaces | TRIM('  Hello  ') → 'Hello' |
| LTRIM(string) | Removes leading spaces | LTRIM('  Hello') → 'Hello' |
| RTRIM(string) | Removes trailing spaces | RTRIM('Hello  ') → 'Hello' |
| REPLACE(string, old, new) | Replaces characters | REPLACE('Hello', 'e', 'a') → 'Hallo' |
| INSTR(string, substring) | Finds position of substring | INSTR('Oracle', 'cle') → 4 |
| LPAD(string, length, pad) | Left pads string | LPAD('5', 3, '0') → '005' |
| RPAD(string, length, pad) | Right pads string | RPAD('5', 3, '0') → '500' |

### Number Functions

| Function | Description | Example |
|----------|-------------|---------|
| ROUND(number, decimals) | Rounds number | ROUND(15.678, 2) → 15.68 |
| TRUNC(number, decimals) | Truncates number | TRUNC(15.678, 2) → 15.67 |
| MOD(m, n) | Returns remainder | MOD(10, 3) → 1 |
| CEIL(number) | Rounds up | CEIL(15.2) → 16 |
| FLOOR(number) | Rounds down | FLOOR(15.8) → 15 |
| ABS(number) | Absolute value | ABS(-15) → 15 |
| POWER(m, n) | m raised to power n | POWER(2, 3) → 8 |
| SQRT(number) | Square root | SQRT(16) → 4 |
| SIGN(number) | Returns sign (-1, 0, 1) | SIGN(-15) → -1 |

### Date Functions

| Function | Description | Example |
|----------|-------------|---------|
| SYSDATE | Current date and time | SYSDATE |
| ADD_MONTHS(date, n) | Adds n months to date | ADD_MONTHS(SYSDATE, 2) |
| MONTHS_BETWEEN(date1, date2) | Months between dates | MONTHS_BETWEEN('01-JUN-23', '01-JAN-23') → 5 |
| NEXT_DAY(date, day) | Next occurrence of day | NEXT_DAY(SYSDATE, 'MONDAY') |
| LAST_DAY(date) | Last day of month | LAST_DAY(SYSDATE) |
| ROUND(date, format) | Rounds date | ROUND(SYSDATE, 'MONTH') |
| TRUNC(date, format) | Truncates date | TRUNC(SYSDATE, 'YEAR') |

### Aggregate Functions

| Function | Description |
|----------|-------------|
| COUNT(*) | Count all rows |
| COUNT(column) | Count non-null values |
| SUM(column) | Sum of values |
| AVG(column) | Average of values |
| MAX(column) | Maximum value |
| MIN(column) | Minimum value |

### Conversion Functions

| Function | Description | Example |
|----------|-------------|---------|
| TO_CHAR(number, format) | Converts number to string | TO_CHAR(5000, 'L9999.99') → Rs5000.00 |
| TO_CHAR(date, format) | Converts date to string | TO_CHAR(SYSDATE, 'DD-MON-YYYY') |
| TO_DATE(string, format) | Converts string to date | TO_DATE('23-12-2020', 'DD-MM-YYYY') |
| TO_NUMBER(string, format) | Converts string to number | TO_NUMBER('123') → 123 |

---

## Constraints

### Types of Constraints

Constraints are rules applied to columns to enforce data integrity.

| Constraint | Description | Example |
|------------|-------------|---------|

| Constraint | Description | Example |
|------------|-------------|---------|
