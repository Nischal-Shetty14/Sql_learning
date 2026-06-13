# SQL String Functions

## LENGTH()

**Definition:** Returns the number of characters in a string.

```sql
SELECT LENGTH('Hello');
```


**Output:**

```text
5
```

---

## UPPER()

**Definition:** Converts all characters to uppercase.

```
SELECT UPPER('hello');
```

**Output:**

```
HELLO
```

---

## LOWER()

**Definition:** Converts all characters to lowercase.

```sql
SELECT LOWER('HELLO');
```

**Output:**

```text
hello
```

---

## TRIM()

**Definition:** Removes spaces from both the beginning and end of a string.

```sql
SELECT TRIM('  Andy  ');
```

**Output:**

```text
Andy
```

---

## LTRIM()

**Definition:** Removes spaces only from the left side of a string.

```sql
SELECT LTRIM('   Andy   ');
```

**Output:**

```text
Andy   
```

---

## RTRIM()

**Definition:** Removes spaces only from the right side of a string.

```sql
SELECT RTRIM('   Andy   ');
```

**Output:**

```text
   Andy
```

---

## LEFT()

**Definition:** Returns a specified number of characters from the left side of a string.

```sql
SELECT LEFT('Leslie', 3);
```

**Output:**

```text
Les
```

---

## RIGHT()

**Definition:** Returns a specified number of characters from the right side of a string.

```sql
SELECT RIGHT('Leslie', 3);
```

**Output:**

```text
lie
```

---

## SUBSTRING()

**Definition:** Extracts a specified portion of a string.

```sql
SELECT SUBSTRING('Leslie', 2, 3);
```

**Output:**

```text
esl
```

---

## REPLACE()

**Definition:** Replaces occurrences of a substring with another substring.

```sql
SELECT REPLACE('Hello World', 'World', 'SQL');
```

**Output:**

```text
Hello SQL
```

---

## LOCATE()

**Definition:** Returns the position of a substring within a string.

```sql
SELECT LOCATE('o', 'Ron');
```

**Output:**

```text
2
```

---

## CONCAT()

**Definition:** Combines two or more strings into a single string.

```sql
SELECT CONCAT('Hello', ' ', 'World');
```

**Output:**

```text
Hello World
```

---

# Common Table Example

```sql
SELECT
    first_name,
    LENGTH(first_name) AS name_length,
    UPPER(first_name) AS upper_name,
    LOWER(first_name) AS lower_name,
    LEFT(first_name, 3) AS first_three_chars,
    RIGHT(first_name, 3) AS last_three_chars
FROM employee_demographics;
```
