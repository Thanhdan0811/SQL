# Database
## Create, use, drop database
- CREATE DATABASE mydb;
- USE mydb;
- DROP DATABASE mydb;

## Alter Database
- only read : ALTER DATABASE mydb READ ONLY = 1 | 0; => can access but not editable or drop.

# Table, column
## create table :

```
CREATE TABLE employees (
  employee_id INT,
  first_name VARCHAR(50),
  last_name VARCHAR(50),
  hourly_paid DECIMAL(5, 2),
  hire_date DATE
);

```

## Select, RENAME, DROP in table
- SELECT * FROM employees;
- RENAME TABLE employees TO workers;
- DROP TABLE employees;

## ALTER TABLE.
```
ALTER TABLE employees
ADD phone_number VARCHAR(15); => add column phone_number

SELECT * FROM employees; // => show employeers table

ALTER TABLE employees
RENAME COLUMN phone_number TO email; // => alter column in table.

ALTER TABLE employees
MODIFY COLUMN email VARCHAR(100); // => alter data type of column.

```

- Move column

```
ALTER TABLE employees
MODIFY email VARCHAR(100)
AFTER last_name; // => move column email to after last_name.

// OR
ALTER TABLE employees
MODIFY email VARCHAR(100)
FIRST; // => move column email become the first column.

```

- DROP column

```
ALTER TABLE employees
DROP COLUMN email; // => remove column email;
```

# ROW COMMAND
