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
- Full Outer join
Left+right join combined,makes a match whenever possible and if not puts in null
```
SELECT *
FROM employee_demographics dem
FULL OUTER JOIN employee_salary sal
ON dem.employee_id = sal.employee_id;
```
```
| employee_id | first_name | age  | occupation | salary |
| ----------- | ---------- | ---- | ---------- | ------ |
| 1           | Leslie     | 44   | Director   | 75000  |
| 2           | Ron        | 55   | Manager    | 70000  |
| 3           | Tom        | 36   | NULL       | NULL   |
| NULL        | NULL       | NULL | Intern     | 20000  |

```
- Cross join
Matches every row of table A with B
Doesnt require ON
```
Example-
employee_demographics
| employee_id | first_name |
| ----------- | ---------- |
| 1           | Leslie     |
| 2           | Ron        |
| 3           | Tom        |

employee_salary
| occupation |
| ---------- |
| Director   |
| Manager    |
| Intern     |
```
```
SELECT *
FROM employee_demographics
CROSS JOIN employee_salary;

output-
| first_name | occupation |
| ---------- | ---------- |
| Leslie     | Director   |
| Leslie     | Manager    |
| Leslie     | Intern     |
| Ron        | Director   |
| Ron        | Manager    |
| Ron        | Intern     |
| Tom        | Director   |
| Tom        | Manager    |
| Tom        | Intern     |
```
- Self Join
A table join with itself.Used when rows inside same table are related
```
| employee_id | employee_name | manager_id |
| ----------- | ------------- | ---------- |
| 1           | Ron           | NULL       |
| 2           | Leslie        | 1          |
| 3           | Tom           | 1          |
| 4           | Andy          | 2          |
Ron has no manager
Leslie and tom have ron as manager
andy has leslie as manager
```
```
SELECT
    emp.employee_name AS Employee,
    mgr.employee_name AS Manager
FROM employee emp
LEFT JOIN employee mgr
ON emp.manager_id = mgr.employee_id;->match employee's manager id with manager's employee id

- Basically they are the same table (emp and mgr(copies)) but we need two so that we can relate it.

Output-
| Employee | Manager |
| -------- | ------- |
| Ron      | NULL    |
| Leslie   | Ron     |
| Tom      | Ron     |
| Andy     | Leslie  |


```
- Natural Join
Joins columns with same name


```
Table A-
| employee_id | name   |
| ----------- | ------ |
| 1           | Leslie |
| 2           | Ron    |
Table B-
| employee_id | salary |
| ----------- | ------ |
| 1           | 75000  |
| 2           | 70000  |
```
```
SELECT *
FROM TableA
NATURAL JOIN TableB;->Sql automatically does ON TableA.employee_id = TableB.employee_id
output-
| employee_id | name   | salary |
| ----------- | ------ | ------ |
| 1           | Leslie | 75000  |
| 2           | Ron    | 70000  |

```


