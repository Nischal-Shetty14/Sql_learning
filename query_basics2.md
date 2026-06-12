# Group By
```
Select gender
from employee_data
GROUP BY gender; ->select statement row has to match the group by row if not using aggregate function
```
-Aggregate functions-AVG,MAX,MIN,COUNT
```
Select gender,avg(age)->returns average age of male and female
from employee_data
GROUP BY gender;
```

#Order By
Arranges in ascending or descending order

```
Select *
from employee_data
ORDER BY age DESC;->arranges according to age in descending
```

# Having
Used with GROUP function and is used after it 

```
Select gender,avg(age)
from employee_data
GROUP BY age
HAVING AVG(AGE)>40;
```
# LIMITS

```
Select * from employee_data
LIMIT 3;->gives 3 rows only
```
- With order by
```
select * from employee_data
order by age desc
limit 2,1->this means select 2 rows and the 1 row after it
```

# Aliasing 
```
select gender,AVG(age) as avg_age
from employee_data
group by gender;->AVG(age) column name will be avg_age
```
