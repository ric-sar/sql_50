* [1378. Replace Employee ID With The Unique Identifier](https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/)

```
SELECT EmployeeUNI.unique_id AS unique_id, Employees.name
FROM Employees
LEFT JOIN EmployeeUNI USING(id);
```

* [1068. Product Sales Analysis I](https://leetcode.com/problems/product-sales-analysis-i/)

```
SELECT p.product_name, s.year, s.price
FROM Product p INNER JOIN Sales s ON p.product_id = s.product_id;
```

* [1581. Customer Who Visited but Did Not Make Any Transactions](https://leetcode.com/problems/customer-who-visited-but-did-not-make-any-transactions/)

```
SElECT v.customer_id, COUNT(*) AS count_no_trans
FROM Visits v
WHERE v.visit_id NOT IN (SELECT visit_id FROM Transactions)
GROUP BY v.customer_id;
```

* [197. Rising Temperature](https://leetcode.com/problems/rising-temperature/)

```
SELECT w2.id
FROM Weather w1, Weather w2
WHERE DATEDIFF(w2.recordDate, w1.recordDate) = 1 AND w2.temperature > w1.temperature;
```

* [1661. Average Time of Process per Machine](https://leetcode.com/problems/average-time-of-process-per-machine/)

```
SELECT a1.machine_id, ROUND(AVG(a2.timestamp - a1.timestamp), 3) AS processing_time
FROM Activity a1
    JOIN Activity a2
    ON a1.process_id = a2.process_id
    AND a1.machine_id = a2.machine_id
    AND a1.timestamp < a2.timestamp
GROUP BY a1.machine_id;
```

* [577. Employee Bonus](https://leetcode.com/problems/employee-bonus/)

```
SELECT e.name, b.bonus
FROM Employee e LEFT OUTER JOIN Bonus b ON e.empId = b.empId
WHERE b.bonus < 1000 or b.bonus IS NULL;
```

* [1280. Students and Examinations](https://leetcode.com/problems/students-and-examinations/)

```
SELECT S.student_id, S.student_name, Sub.subject_name, COUNT(E.subject_name) AS attended_exams
FROM Students S CROSS JOIN Subjects Sub LEFT OUTER JOIN Examinations E
    ON S.student_id = E.student_id
    AND Sub.subject_name = E.subject_name
GROUP BY S.student_id, S.student_name, Sub.subject_name
ORDER BY S.student_id, Sub.subject_name;
```

* [570. Managers with at Least 5 Direct Reports](https://leetcode.com/problems/managers-with-at-least-5-direct-reports/)

```
SELECT e1.name
FROM Employee e1 JOIN Employee e2 ON e1.id = e2.managerId
GROUP BY e1.id
HAVING count(e2.managerId) >= 5;
```

* [1934. Confirmation Rate](https://leetcode.com/problems/confirmation-rate/)

```
SELECT s.user_id, ROUND(AVG(CASE WHEN c.action = 'confirmed' THEN 1.00 ELSE 0.00 END), 2) AS confirmation_rate
FROM signups s LEFT JOIN confirmations c ON s.user_id= c.user_id
GROUP BY s.user_id;;
```
