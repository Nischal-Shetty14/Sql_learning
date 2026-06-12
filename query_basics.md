# Select
Used to select rows 
Select * selects everything
```
pattern-
Select * from table_name;
Specific-
Select row1,row2 from table_name;
```

# Distinct
```
Select distinct gender from table;
```
->returns only male and female

But if two rows-
```
Select distinct name,gender from table;
->It wont just return male or female it will consider both name and gender and then see if they are distinct or not
```

# Where
Returns row which fulfils specific conditions

```
Select *
from employee_data
where name='Nischal';
```
- Can use >,<,=,!=
- Logical operators-AND,OR,OR NOT
```
Select *
from employee_data
where age>40 AND gender='male'
```
-LIKE
```
Select *
from employee_data
where name LIKE 'jer%'->MEANS that jer should be there but after that anything can come
```
