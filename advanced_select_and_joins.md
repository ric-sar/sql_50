# Advanced Select and Joins

* [1731. The Number of Employees Which Report to Each Employee](https://leetcode.com/problems/the-number-of-employees-which-report-to-each-employee/)

```
SELECT e1.employee_id, e1.name, COUNT(e2.employee_id) AS reports_count, ROUND(AVG(e2.age)) AS average_age
FROM employees e1 JOIN employees e2 ON e1.employee_id = e2.reports_to
GROUP BY employee_id
ORDER BY employee_id;
```

* [1789. Primary Department for Each Employee](https://leetcode.com/problems/primary-department-for-each-employee/)

```
SELECT employee_id, department_id
FROM employee
GROUP BY employee_id
HAVING COUNT(employee_id) = 1
UNION
SELECT employee_id, department_id
FROM employee
WHERE primary_flag = 'Y';
```

* [610. Triangle Judgement](https://leetcode.com/problems/triangle-judgement/)

```
SELECT x, y, z, (CASE WHEN (x+y) > z AND (x+z) > y AND (y+z) > x THEN 'Yes' ELSE 'No' END) AS triangle
FROM Triangle;
```

* [180. Consecutive Numbers](https://leetcode.com/problems/find-followers-count/)

```
SELECT DISTINCT num AS ConsecutiveNums
FROM Logs
WHERE (id + 1, num) IN (SELECT * FROM Logs) AND (id + 2, num) IN (SELECT * FROM Logs);
```

* [1164. Product Price at a Given Date](https://leetcode.com/problems/product-price-at-a-given-date/)

```
SELECT product_id, new_price AS price
FROM Products
WHERE (product_id, change_date) 
IN (
  SELECT product_id, MAX(change_date) FROM Products
  WHERE change_date <= '2019-08-16' GROUP BY product_id
  )
UNION
SELECT product_id, 10 AS price
FROM Products
GROUP BY product_id
HAVING MIN(change_date) > '2019-08-16';
```

* [1204. Last Person to Fit in the Bus](https://leetcode.com/problems/last-person-to-fit-in-the-bus/)

```
SELECT person_name
from (
    SELECT person_id,
    person_name,
    weight,
    turn,
    SUM(weight) OVER (ORDER BY turn) AS CumulativeSum
    FROM Queue
    ORDER BY turn DESC) AS temp
WHERE CumulativeSum <= 1000
LIMIT 1;
```

* [1907. Count Salary Categories](https://leetcode.com/problems/count-salary-categories/)

```
SELECT "Low Salary" AS category,
       SUM(income < 20000) AS accounts_count
  FROM Accounts
UNION
SELECT "Average Salary" AS category,
       SUM(income BETWEEN 20000 AND 50000) AS accounts_count
  FROM Accounts
UNION
SELECT "High Salary" AS category,
       SUM(income > 50000) AS accounts_count
  FROM Accounts;
```
