# Regex
More powerful version of LIKE
can check digits,character ranges,start/end of string
```
- WHERE code REGEXP '[0-9]{4}'->0 to 9,4 numbers from it
- WHERE name REGEXP '^A'->starts with A
- WHERE email REGEXP '\\.com$'->ends with .com($ means end of string)
- WHERE value REGEXP '^[0-9]+$'->Only digits(+ means one character atleast has to match
```
