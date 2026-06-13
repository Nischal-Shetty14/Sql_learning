Join combines columns and Union combines row
Stack one on top of each other
- Union/Union distinct
Combines rows and removes duplicates
```
employee_2024
| name   |
| ------ |
| Ron    |
| Leslie |
| Tom    |
employee_2025
| name  |
| ----- |
| Tom   |
| Andy  |
| April |
```
```
SELECT name FROM employees_2024
UNION
SELECT name FROM employees_2025;

output-
| name   |
| ------ |
| Ron    |
| Leslie |
| Tom    |
| Andy   |
| April  |

```
- Union all
No duplicate removal
```
SELECT name FROM employees_2024
UNION ALL
SELECT name FROM employees_2025;

Result-
| name   |
| ------ |
| Ron    |
| Leslie |
| Tom    |
| Tom    |
| Andy   |
| April  |

```


