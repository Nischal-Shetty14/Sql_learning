# Joins
```
employee_demographics
| employee_id | first_name | age |
| ----------- | ---------- | --- |
| 1           | Leslie     | 44  |
| 2           | Ron        | 55  |
| 3           | Tom        | 36  |

employee_salary
| employee_id | occupation | salary |
| ----------- | ---------- | ------ |
| 1           | Director   | 75000  |
| 2           | Manager    | 70000  |
| 4           | Intern     | 20000  |
```

- Inner join
Returns only matching rows from both tables(Intersection basically)
```
SELECT *
FROM employee_demographics dem
INNER JOIN employee_salary sal
    ON dem.employee_id = sal.employee_id;
```
```
Result-
| employee_id | first_name | occupation |
| ----------- | ---------- | ---------- |
| 1           | Leslie     | Director   |
| 2           | Ron        | Manager    |

```
- Left join
Returns all row from left and matching rows from right
```
SELECT *
FROM employee_demographics dem
LEFT JOIN employee_salary sal
    ON dem.employee_id = sal.employee_id;
```
```
Result-
| employee_id | first_name | occupation |
| ----------- | ---------- | ---------- |
| 1           | Leslie     | Director   |
| 2           | Ron        | Manager    |
| 3           | Tom        | NULL       |
```
- Right join
All rows from right and matching from left
```
SELECT *
FROM employee_demographics dem
RIGHT JOIN employee_salary sal
    ON dem.employee_id = sal.employee_id;
```
```
| employee_id | first_name | occupation |
| ----------- | ---------- | ---------- |
| 1           | Leslie     | Director   |
| 2           | Ron        | Manager    |
| NULL        | NULL       | Intern     |

```
- 
