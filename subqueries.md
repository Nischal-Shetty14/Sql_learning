Sql version of if else statements
```
SELECT column_name,
       CASE
           WHEN condition1 THEN result1
           WHEN condition2 THEN result2
           ELSE result3
       END
FROM table_name;
```
```

| first_name | age |
| ---------- | --- |
| Leslie     | 44  |
| Ron        | 55  |
| Tom        | 36  |
| April      | 25  |

query-
SELECT first_name,age,
       CASE
           WHEN age < 30 THEN 'Young'
           WHEN age BETWEEN 30 AND 50 THEN 'Adult'
           ELSE 'Senior'
       END AS Age_Group
FROM employee_demographics;

output-
| first_name | age | Age_Group |
| ---------- | --- | --------- |
| Leslie     | 44  | Adult     |
| Ron        | 55  | Senior    |
| Tom        | 36  | Adult     |
| April      | 25  | Young     |

```

**CASE stops at the first true condition**
