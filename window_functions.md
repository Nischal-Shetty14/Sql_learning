A window function performs calculation across set of rows while keeping the rows visible.
- Aggregate functions return one result only and we lose other rows
```
SELECT SUM(salary)
FROM employees;

output-| SUM    |
| ------ |
| 180000 |

```
- Structure-
```
Function() Over()->over is basically on which rows should i perform this if () then all rows
eg-
ROW_NUMBER() OVER(...)
RANK() OVER(...)
SUM(salary) OVER(...)
AVG(salary) OVER(...)
```
- Over components-
  - Partition by=group by but without removing rows
    ```
    ROW_NUMBER()
    OVER(PARTITION BY gender)

    internally creates
    Female partition-
    | Leslie |
    | ------ |
    | Donna  |
    Male partition-
    | Chris |
    | ----- |
    | Ben   |
  - Order by=controls order inside each partition
    ```
    ROW_NUMBER()
    OVER(
    PARTITION BY gender
    ORDER BY salary DESC
    )
    This first creates partition as seen before and then orders them in descending order
    Female-

    | Name   | Salary |
    | ------ | ------ |
    | Leslie | 75000  |
    | Donna  | 60000  |

    Male-
    | Name  | Salary |
    | ----- | ------ |
    | Chris | 90000  |
    | Ben   | 70000  |
    ```

  Examples-
  - Row_number()
```
  SELECT first_name,
       salary,
       ROW_NUMBER()
       OVER(
           PARTITION BY gender
           ORDER BY salary DESC
       ) AS row_num
  FROM employee_salary;

  o/p-
Female
  | Name   | Salary | Row Number |
| ------ | ------ | ---------- |
| Leslie | 75000  | 1          |
| Donna  | 60000  | 2          |
| Ann    | 55000  | 3          |
| April  | 25000  | 4          |

Male
| Name  | Salary | Row Number |
| ----- | ------ | ---------- |
| Chris | 90000  | 1          |
| Ben   | 70000  | 2          |
| Craig | 65000  | 3          |
| Mark  | 57000  | 4          |
| Tom   | 50000  | 5          |
| Jerry | 50000  | 6          |
| Andy  | 20000  | 7          |
```
- Rank()
```
Same as row number but if same salary then same rank
| Name  | Salary | Rank |
| ----- | ------ | ---- |
| Chris | 90000  | 1    |
| Ben   | 70000  | 2    |
| Craig | 65000  | 3    |
| Mark  | 57000  | 4    |
| Tom   | 50000  | 5    |
| Jerry | 50000  | 5    |
| Andy  | 20000  | 7    |->6 is skipped
```
- Dense_Rank()
```
Same as rank but no number skipped
| Name  | Salary | Dense Rank |
| ----- | ------ | ---------- |
| Chris | 90000  | 1          |
| Ben   | 70000  | 2          |
| Craig | 65000  | 3          |
| Mark  | 57000  | 4          |
| Tom   | 50000  | 5          |
| Jerry | 50000  | 5          |
| Andy  | 20000  | 6          |
```
- Sum
```
SELECT first_name,
       salary,
       SUM(salary) OVER()
FROM employee_salary;

o/p-
| Name   | Salary | Total  |
| ------ | ------ | ------ |
| Leslie | 75000  | 617000 |
| Donna  | 60000  | 617000 |
| Chris  | 90000  | 617000 |

```
- Sum with partition
```
SELECT first_name,
       gender,
       salary,
       SUM(salary)
       OVER(PARTITION BY gender)
FROM employee_salary;
o/p-
| Name   | Gender | Salary | Total Gender Salary |
| ------ | ------ | ------ | ------------------- |
| Leslie | Female | 75000  | 215000              |
| Donna  | Female | 60000  | 215000              |
| Chris  | Male   | 90000  | 402000              |
```
- Lead() and LAG()
Look at next and previous salary respectively
```
LEAD(salary)
OVER(ORDER BY salary)

o/p-
| Salary | Next Salary |
| ------ | ----------- |
| 25000  | 50000       |
| 50000  | 70000       |
| 70000  | NULL        |

```
```
LAG(salary)
OVER(ORDER BY salary)

o/p-
| Salary | Previous Salary |
| ------ | --------------- |
| 25000  | NULL            |
| 50000  | 25000           |
| 70000  | 50000           |

```






