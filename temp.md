Temp table exists only temporarily during a session or procedure
Syntax-
```
CREATE TABLE #ITEmployees
(
    ID INT,
    Name VARCHAR(50),
    Salary INT
);
or
CREATE TEMPORARY TABLE ITemployees
```
Inserting-
```
INSERT INTO #ITEmployees
SELECT ID, Name, Salary
FROM Employees
WHERE Department='IT';
```
Using it-
```
SELECT AVG(Salary)
FROM #ITEmployees;
```
We dont query Employees everytime coz it runs many times if we only want to retrieve a thing which is commonly operated upon
- Local vs Global temp tables
local-#temp-only our session can see it.Gone after disconnection
global-##temp-visible to everyone.disconnects only when all users disconnect

- CTE vs TEMP
Cte exists only for the query and temp stays for the session.that means we can't operate or update cte's much whereas we can with temp
A CTE can only be referenced by the statement immediately following it.
- Use a CTE when:
The logic is simple.
You're writing one query.
You want the query to be readable.
You don't need to modify the intermediate result.
- Use a Temp Table when:
The result will be reused across multiple SQL statements.
You need to UPDATE, DELETE, or INSERT into the intermediate data.
The intermediate result is very large and worth storing once.
You want to create indexes on the intermediate result.
You're writing a stored procedure with several steps.
