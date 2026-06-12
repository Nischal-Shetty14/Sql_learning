## 1. Create a Database

Creates a new database.

```sql
CREATE DATABASE Parks_and_Recreation;
```

### Use the Database

```sql
USE Parks_and_Recreation;
```

---

## 2. Drop a Database

Deletes the entire database permanently.

```sql
DROP DATABASE Parks_and_Recreation;
```

### Safer Version

```sql
DROP DATABASE IF EXISTS Parks_and_Reation;
```

---

## 3. Create a Table

Syntax:

```sql
CREATE TABLE table_name (
    column_name datatype constraints
);
```

Example:

```sql
CREATE TABLE employee_demographics (
    employee_id INT NOT NULL,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    age INT,
    gender VARCHAR(10),
    birth_date DATE,
    PRIMARY KEY (employee_id)
);
```
