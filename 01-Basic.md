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

## Insert Row

```
insert into employees
values ( 1, "Dan", "Nguyen", 25.50,  "2023-01-02");
select * from employees;
```

- multiple rows insert

```
insert into employees
values ( 1, "Dan", "Nguyen", 25.50,  "2023-01-02"),
	   ( 2, "Van", "Le", 15.00, "2023-01-03"),
       ( 3, "Toan", "Duong", 20.12, "2023-01-04"),
       ( 4, "Sơn", "Dang", 20.12, "2023-01-04");

```

- Insert with missing data. (missing data will be null).

```
insert into employees (employee_id, first_name, last_name)
values ( 1, "Dan", "Nguyen", );
```

## select 
- Select column
```
select first_name, last_name from employees;
select last_name, first_name from employees;
```

- select with specific.

```
select * from employees where employee_id = 1;
select * from employees where employee_id != 1;
select last_name from employees where employee_id = 1;
select * from employees where hourly_paid <= 20.12;

select * from employees where hire_date IS NULL; // => show all results that have hire_date is NULL
select * from employees where hire_date IS NOT NULL; // => show all results that have hire_date is NOT NULL

```

## Update row
```
update employees 
set  hourly_paid = 20.25,
     hire_date = "2023-01-06"
where employee_id = 6;
select * from employees;
```

- Set to null
```
update employees 
set  hourly_paid = 20.25,
     hire_date = NULL
where employee_id = 6;
select * from employees;
```

- No specific the where, it will set value for all rows.
```
update employees 
set  hourly_paid = 20.25;
select * from employees;

```

## DELETE ROWS
```
delete from employees; // => will delete all rows.
=====================

delete from employees
where employee_id = 6;
select * from employees;

```

# AUTOCOMMIT, COMMIT, ROLLBACK
- AUTOCOMMIT will auto save commit when perform a transaction.
```
SET AUTOCOMMIT = OFF;
```
- COMMIT : set commit mannual.
```
COMMIT;
```
- ROLLBACK : restore current transaction back to the previous save point.
```
delete from employees;
select * from employees;
rollback;
select * from employees;
```


