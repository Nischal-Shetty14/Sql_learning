CTE or common table expression is a temporary named result table that exists for only one query
Why use a CTE?
Without a CTE, you might have to write a long query again and again.
A CTE lets you:

- Write a query once.
- Give it a name.
- Use it like a table in the main query.

Cte with aggregation-
```
WITH SalaryStats AS
(
    SELECT gender,
           AVG(salary) avg_sal
    FROM employee_salary
    GROUP BY gender
)
SELECT *
FROM SalaryStats;

| gender | avg_sal |
| ------ | ------- |
| Male   | 60000   |
| Female | 70000   |

```
Using the result again-
```
WITH SalaryStats AS
(
    SELECT gender,
           AVG(salary) avg_sal
    FROM employee_salary
    GROUP BY gender
)
SELECT AVG(avg_sal)
FROM SalaryStats;

65000
````
