# Window functions
Window functions exist so that after a query on a table is run the rows dont collapse
```
Normal-
| name  | dept | salary |
| ----- | ---- | ------ |
| Tom   | IT   | 40000  |
| Jerry | IT   | 60000  |
| Alex  | HR   | 70000  |
| Ben   | HR   | 50000  |

with temp-
| name  | salary | average |
| ----- | ------ | ------- |
| Tom   | 40000  | 55000   |
| Jerry | 60000  | 55000   |
| Alex  | 70000  | 55000   |
| Ben   | 50000  | 55000   |
```
Syntax-
```
function()

OVER(...)
```
example-
```
SELECT
name,
salary,
AVG(salary) OVER()
FROM employee_salary;
```
- Group by is many rows->one row
- Temp table is many->many

- Partition by
Does group by internally while keeping window functionality
```
SELECT name,dept,salary,

AVG(salary)
OVER(PARTITION BY dept)

FROM employee_salary;

output-
| name  | dept | salary |
| ----- | ---- | ------ |
| Tom   | IT   | 40000  |
| Jerry | IT   | 60000  |
| Alex  | HR   | 70000  |
| Ben   | HR   | 50000  |

```
- Row_number()
```
SELECT name,salary,ROW_NUMBER()
OVER(ORDER BY salary DESC)

FROM employee_salary;

output-| name  | salary | row_number |
| ----- | ------ | ---------- |
| Alex  | 70000  | 1          |
| Jerry | 60000  | 2          |
| Ben   | 50000  | 3          |
| Tom   | 40000  | 4          |

```
- RANK()
```
RANK()
OVER(ORDER BY salary DESC)
o/p-
| salary | rank |
| ------ | ---- |
| 70000  | 1    |
| 60000  | 2    |
| 60000  | 2    |
| 40000  | 4    |

```
- DENSE_RANK()
No skipping
```
| salary | dense_rank |
| ------ | ---------- |
| 70000  | 1          |
| 60000  | 2          |
| 60000  | 2          |
| 40000  | 3          |
```
- RUNNING TOTAL
```
SELECT month,sales,

SUM(sales)
OVER(
ORDER BY month
)

FROM sales;

| month | sales | running_total |
| ----- | ----- | ------------- |
| Jan   | 100   | 100           |
| Feb   | 200   | 300           |
| Mar   | 150   | 450           |


```
- LAG() and LEAD()
lag gives us value of previous row and lead gives of next row
lag-
```
| Month | Sales | Previous |
| ----- | ----- | -------- |
| Jan   | 100   | NULL     |
| Feb   | 200   | 100      |
| Mar   | 150   | 200      |
```
lead-
```
| Month | Sales | Next |
| ----- | ----- | ---- |
| Jan   | 100   | 200  |
| Feb   | 200   | 150  |
| Mar   | 150   | NULL |
```
