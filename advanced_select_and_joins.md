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
```

* [1204. Last Person to Fit in the Bus](https://leetcode.com/problems/last-person-to-fit-in-the-bus/)

```
```

* [1907. Count Salary Categories](https://leetcode.com/problems/count-salary-categories/)

```
```
