A window function performs calculation across set of rows while keeping the rows visible.
- Aggregate functions return one result only and we lose other rows
```
SELECT SUM(salary)
FROM employees;

output-| SUM    |
| ------ |
| 180000 |

```
- Structure-Function() Over()

