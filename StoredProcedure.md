It is like a function->It is a saved sql program inside the database
If we are doing something everyday or very frequently then we save or store it so that dont have to do it again and again
eg-
```
CREATE PROCEDURE GetEmployees
AS
BEGIN
    SELECT *
    FROM Employees;
END;

** EXECUTING **-
EXEC GetEmployees;
```
- Procedure with parameters
If multiple things are required such as multiple departments-
GetITEmployees
GetSalesEmployees
GetHREmployees
```
CREATE PROCEDURE GetDepartment
@Dept VARCHAR(20)
AS
BEGIN
    SELECT *
    FROM Employees
    WHERE Department=@Dept;
END;

EXEC GetDepartment 'IT' or EXEC GetDepartment 'Sales';
```
- Multiple parameters
```
CREATE PROCEDURE GetEmployees
@Dept VARCHAR(20),
@Salary INT
AS
BEGIN
SELECT *
FROM Employees
WHERE Department=@Dept
AND Salary>@Salary;
END;

EXEC GetEmployees 'IT',70000;
```
- Variables inside procedure.
 ```
 DECLARE @AvgSalary INT;

SET @AvgSalary=
(
SELECT AVG(Salary)
FROM Employees
);

SELECT *
FROM Employees
WHERE Salary>@AvgSalary;
```

