CTE or common table expression is a temporary named result table that exists for only one query
Why use a CTE?
Without a CTE, you might have to write a long query again and again.
A CTE lets you:

- Write a query once.
- Give it a name.
- Use it like a table in the main query.
- Temporary name for a query
- Syntax-
```
WITH name AS
(
    query
)

SELECT ...
FROM name;
```

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
- We could create table but why to waste space on that,cte is like a variable x=10 where it exists for the period of program existing
- Multiple CTEs
```
WITH dept_avg AS
(
    SELECT dept,
           AVG(salary) avg_sal
    FROM employee_salary
    GROUP BY dept
),

high_dept AS
(
    SELECT *
    FROM dept_avg
    WHERE avg_sal > 55000
)

SELECT *
FROM high_dept;
```
- Recursive CTE
```
  WITH RECURSIVE numbers AS
(
    SELECT 1

    UNION ALL

    SELECT number + 1
    FROM numbers
    WHERE number < 5
)

SELECT *
FROM numbers;
```
