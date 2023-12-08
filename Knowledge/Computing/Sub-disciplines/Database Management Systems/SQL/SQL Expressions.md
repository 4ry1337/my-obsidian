# [[Structured Query Language | SQL]] Expressions
## CASE (IF/ELSE)
The `CASE` expression goes through conditions and returns a value when the first condition is met (like an if-then-else statement). So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the `ELSE` clause.
```SQL
CASE expression
    WHEN condition_1 THEN result_1
    WHEN condition_2 THEN result_2
    ...  
    WHEN condition_N THEN result_N
    ELSE result  
END;
```