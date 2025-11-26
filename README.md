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

| PRIMARY KEY | Uniquely identifies each record | emp_id NUMBER PRIMARY KEY |
| FOREIGN KEY | Links to primary key in another table | dept_id REFERENCES dept(dept_id) |
| UNIQUE | Ensures all values are different | email VARCHAR2(50) UNIQUE |
| NOT NULL | Column cannot contain NULL values | name VARCHAR2(50) NOT NULL |
| CHECK | Validates data based on condition | age NUMBER CHECK(age >= 18) |
| DEFAULT | Sets default value if none provided | status VARCHAR2(10) DEFAULT 'Active' |

### Constraint Levels

**Column Level Constraint**: Defined within column definition
```sql
CREATE TABLE emp (
    emp_id NUMBER(4) PRIMARY KEY,
    emp_name VARCHAR2(20) NOT NULL
);
```

**Table Level Constraint**: Defined after all columns
```sql
CREATE TABLE emp (
    emp_id NUMBER(4),
    emp_name VARCHAR2(20),
    CONSTRAINT emp_pk PRIMARY KEY(emp_id)
);
```

---

## Database Objects

### Views

A view is a virtual table based on SQL query result.

```sql
-- Creating View
CREATE VIEW emp_view AS
SELECT empno, ename, sal FROM emp WHERE deptno = 10;

-- Using View
SELECT * FROM emp_view;

-- Dropping View
DROP VIEW emp_view;
```

### Indexes

Indexes improve query performance.

```sql
-- Creating Index
CREATE INDEX idx_ename ON emp(ename);

-- Dropping Index
DROP INDEX idx_ename;
```

### Sequences

Generates unique numbers automatically.

```sql
-- Creating Sequence
CREATE SEQUENCE emp_seq
START WITH 1
INCREMENT BY 1;

-- Using Sequence
INSERT INTO emp VALUES(emp_seq.NEXTVAL, 'John', 'CLERK');

-- Get Current Value
SELECT emp_seq.CURRVAL FROM dual;
```

### Synonyms

Alternative names for database objects.

```sql
-- Creating Synonym
CREATE SYNONYM e FOR emp;

-- Using Synonym
SELECT * FROM e;
```

---

## PL/SQL Basics

### What is PL/SQL?

- PL/SQL stands for Procedural Language/SQL
- Extension of SQL with procedural features
- Supports variables, conditions, loops, and exception handling

### Structure of PL/SQL Block

```sql
DECLARE
    -- Variable declarations
BEGIN
    -- Executable statements
EXCEPTION
    -- Exception handling
END;
```

### Variables

```sql
DECLARE
    v_name VARCHAR2(50);
    v_sal NUMBER(10,2) := 5000;
    v_hiredate DATE := SYSDATE;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Salary: ' || v_sal);
END;
```

### %TYPE and %ROWTYPE

```sql
-- %TYPE: Takes datatype from column
DECLARE
    v_sal emp.sal%TYPE;
BEGIN
    SELECT sal INTO v_sal FROM emp WHERE empno = 7369;
END;

-- %ROWTYPE: Takes structure of entire row
DECLARE
    v_emp emp%ROWTYPE;
BEGIN
    SELECT * INTO v_emp FROM emp WHERE empno = 7369;
END;
```

---

## Control Structures

### IF Statement

```sql
DECLARE
    v_sal NUMBER := 5000;
BEGIN
    IF v_sal > 3000 THEN
        DBMS_OUTPUT.PUT_LINE('High Salary');
    ELSIF v_sal > 1000 THEN
        DBMS_OUTPUT.PUT_LINE('Medium Salary');
    ELSE
        DBMS_OUTPUT.PUT_LINE('Low Salary');
    END IF;
END;
```

### CASE Statement

```sql
DECLARE
    v_grade CHAR(1) := 'A';
BEGIN
    CASE v_grade
        WHEN 'A' THEN DBMS_OUTPUT.PUT_LINE('Excellent');
        WHEN 'B' THEN DBMS_OUTPUT.PUT_LINE('Good');
        ELSE DBMS_OUTPUT.PUT_LINE('Average');
    END CASE;
END;
```

### LOOP Statements

**Simple LOOP**
```sql
DECLARE
    v_counter NUMBER := 1;
BEGIN
    LOOP
        DBMS_OUTPUT.PUT_LINE(v_counter);
        v_counter := v_counter + 1;
        EXIT WHEN v_counter > 5;
    END LOOP;
END;
```

**WHILE LOOP**
```sql
DECLARE
    v_counter NUMBER := 1;
BEGIN
    WHILE v_counter <= 5 LOOP
        DBMS_OUTPUT.PUT_LINE(v_counter);
        v_counter := v_counter + 1;
    END LOOP;
END;
```

**FOR LOOP**
```sql
BEGIN
    FOR i IN 1..5 LOOP
        DBMS_OUTPUT.PUT_LINE(i);
    END LOOP;
END;
```

---

## Cursors

### What are Cursors?

Cursors are used to process multiple rows returned by SELECT statement.

### Implicit Cursors

Automatically created by Oracle for DML statements.

```sql
BEGIN
    UPDATE emp SET sal = sal * 1.1 WHERE deptno = 10;
    DBMS_OUTPUT.PUT_LINE(SQL%ROWCOUNT || ' rows updated');
END;
```

### Explicit Cursors

```sql
DECLARE
    CURSOR emp_cur IS SELECT empno, ename, sal FROM emp;
    v_empno emp.empno%TYPE;
    v_ename emp.ename%TYPE;
    v_sal emp.sal%TYPE;
BEGIN
    OPEN emp_cur;
    LOOP
        FETCH emp_cur INTO v_empno, v_ename, v_sal;
        EXIT WHEN emp_cur%NOTFOUND;
        DBMS_OUTPUT.PUT_LINE(v_ename || ' - ' || v_sal);
    END LOOP;
    CLOSE emp_cur;
END;
```

### Cursor FOR LOOP

```sql
DECLARE
    CURSOR emp_cur IS SELECT empno, ename, sal FROM emp;
BEGIN
    FOR emp_rec IN emp_cur LOOP
        DBMS_OUTPUT.PUT_LINE(emp_rec.ename || ' - ' || emp_rec.sal);
    END LOOP;
END;
```

---

## Exception Handling

### Predefined Exceptions

```sql
DECLARE
    v_sal emp.sal%TYPE;
BEGIN
    SELECT sal INTO v_sal FROM emp WHERE empno = 9999;
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('Employee not found');
    WHEN TOO_MANY_ROWS THEN
        DBMS_OUTPUT.PUT_LINE('Multiple rows returned');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
END;
```

### User-Defined Exceptions

```sql
DECLARE
    v_sal emp.sal%TYPE;
    low_salary EXCEPTION;
BEGIN
    SELECT sal INTO v_sal FROM emp WHERE empno = 7369;
    IF v_sal < 1000 THEN
        RAISE low_salary;
    END IF;
EXCEPTION
    WHEN low_salary THEN
        DBMS_OUTPUT.PUT_LINE('Salary is too low');
END;
```

---

## Collections

### Types of Collections

1. **Associative Arrays (Index-By Tables)**
2. **Nested Tables**
3. **VARRAYs**

### Associative Array

```sql
DECLARE
    TYPE name_table IS TABLE OF VARCHAR2(50) INDEX BY PLS_INTEGER;
    names name_table;
BEGIN
    names(1) := 'John';
    names(2) := 'Mary';
    names(3) := 'Peter';
    
    FOR i IN 1..3 LOOP
        DBMS_OUTPUT.PUT_LINE(names(i));
    END LOOP;
END;
```

### Nested Table

```sql
DECLARE
    TYPE name_table IS TABLE OF VARCHAR2(50);
    names name_table := name_table('John', 'Mary', 'Peter');
BEGIN
    FOR i IN 1..names.COUNT LOOP
        DBMS_OUTPUT.PUT_LINE(names(i));
    END LOOP;
END;
```

---

## Stored Procedures & Functions

### Procedures

```sql
-- Creating Procedure
CREATE OR REPLACE PROCEDURE increase_salary(
    p_empno IN NUMBER,
    p_amount IN NUMBER
)
IS
BEGIN
    UPDATE emp SET sal = sal + p_amount WHERE empno = p_empno;
    COMMIT;
END;

-- Calling Procedure
EXECUTE increase_salary(7369, 500);
```

### Functions

```sql
-- Creating Function
CREATE OR REPLACE FUNCTION get_salary(p_empno NUMBER)
RETURN NUMBER
IS
    v_sal emp.sal%TYPE;
BEGIN
    SELECT sal INTO v_sal FROM emp WHERE empno = p_empno;
    RETURN v_sal;
END;

-- Calling Function
SELECT get_salary(7369) FROM dual;
```

---

## Packages

### What is a Package?

A package is a schema object that groups logically related PL/SQL types, variables, procedures, and functions.

### Package Specification

```sql
CREATE OR REPLACE PACKAGE emp_pkg IS
    PROCEDURE hire_employee(p_empno NUMBER, p_ename VARCHAR2);
    FUNCTION get_salary(p_empno NUMBER) RETURN NUMBER;
END emp_pkg;
```

### Package Body

```sql
CREATE OR REPLACE PACKAGE BODY emp_pkg IS
    PROCEDURE hire_employee(p_empno NUMBER, p_ename VARCHAR2) IS
    BEGIN
        INSERT INTO emp(empno, ename) VALUES(p_empno, p_ename);
        COMMIT;
    END;
    
    FUNCTION get_salary(p_empno NUMBER) RETURN NUMBER IS
        v_sal emp.sal%TYPE;
    BEGIN
        SELECT sal INTO v_sal FROM emp WHERE empno = p_empno;
        RETURN v_sal;
    END;
END emp_pkg;
```

---

## Triggers

### What is a Trigger?

A trigger is a stored program that automatically executes when a specific event occurs.

### Types of Triggers

1. **DML Triggers** - BEFORE/AFTER INSERT, UPDATE, DELETE
2. **DDL Triggers** - CREATE, ALTER, DROP
3. **System Triggers** - LOGON, LOGOFF

### DML Trigger Example

```sql
CREATE OR REPLACE TRIGGER emp_audit_trigger
BEFORE INSERT OR UPDATE ON emp
FOR EACH ROW
BEGIN
    :NEW.modified_date := SYSDATE;
    
    IF INSERTING THEN
        DBMS_OUTPUT.PUT_LINE('New employee inserted');
    ELSIF UPDATING THEN
        DBMS_OUTPUT.PUT_LINE('Employee updated');
    END IF;
END;
```

### Audit Trigger Example

```sql
CREATE TABLE emp_audit (
    empno NUMBER,
    old_sal NUMBER,
    new_sal NUMBER,
    modified_by VARCHAR2(50),
    modified_date DATE
);

CREATE OR REPLACE TRIGGER emp_salary_audit
AFTER UPDATE OF sal ON emp
FOR EACH ROW
BEGIN
    INSERT INTO emp_audit VALUES(
        :OLD.empno,
        :OLD.sal,
        :NEW.sal,
        USER,
        SYSDATE
    );
END;
```

---

## Conclusion

This guide covers comprehensive Oracle SQL and PL/SQL concepts including:

- SQL fundamentals and commands
- Data types and table operations
- Joins, subqueries, and built-in functions
- Constraints and database objects
- PL/SQL programming basics
- Control structures and cursors
- Exception handling and collections
- Stored procedures, functions, packages, and triggers

Practice these concepts regularly to master Oracle database development!
