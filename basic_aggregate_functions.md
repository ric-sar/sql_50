# Basic Aggregate Functions

* [620. Not Boring Movies](https://leetcode.com/problems/not-boring-movies/)

```
SELECT *
FROM Cinema
WHERE MOD(id, 2) = 1 AND description <> 'boring'
ORDER BY rating DESC;
```

* [1251. Average Selling Price](https://leetcode.com/problems/average-selling-price/)
```
SELECT p.product_id, ROUND(SUM(u.units*p.price)/sum(u.units), 2) AS average_price
FROM Prices p LEFT JOIN UnitsSold u ON  p.product_id = u.product_id
AND u.purchase_date between p.Start_date AND p.end_date
GROUP BY p.product_id;
```

* [1075. Project Employees I](https://leetcode.com/problems/project-employees-i/)

```
SELECT p.project_id, ROUND(SUM(e.experience_years)/COUNT(e.employee_id), 2) AS average_years
FROM Project p
    LEFT JOIN
    Employee e ON p.employee_id = e.employee_id
GROUP BY p.project_id;
```

* [1633. Percentage of Users Attended a Contest](https://leetcode.com/problems/percentage-of-users-attended-a-contest/)

```
SELECT contest_id, ROUND(COUNT(distinct user_id) /(SELECT COUNT(user_id) FROM Users)*100,2) AS percentage
FROM Register
GROUP BY contest_id
ORDER BY percentage DESC, contest_id;
```

* [1211. Queries Quality and Percentage](https://leetcode.com/problems/queries-quality-and-percentage/)

```
SELECT query_name, ROUND(AVG(rating/position), 2) AS quality, ROUND(SUM(rating < 3)/COUNT(query_name)*100, 2) AS poor_query_percentage
FROM Queries
GROUP BY query_name;
```

* [1193. Monthly Transactions I](https://leetcode.com/problems/monthly-transactions-i/)

```
SELECT DATE_FORMAT(trans_date, '%Y-%m') AS month,
  country,
  COUNT(id) AS trans_count,
  SUM(CASE WHEN state = 'approved' THEN 1 ELSE 0 END) AS approved_count,
  SUM(amount) AS trans_total_amount,
  SUM(CASE WHEN state = 'approved' THEN amount ELSE 0 END) AS approved_total_amount
FROM Transactions
GROUP BY month, country;
```

* [1174. Immediate Food Delivery II](https://leetcode.com/problems/immediate-food-delivery-ii/)

```
SELECT ROUND(AVG(CASE WHEN order_date = customer_pref_delivery_date THEN 1 ELSE 0 END)*100 , 2) AS immediate_percentage
FROM Delivery
WHERE (customer_id, order_date) IN 
  (SELECT customer_id, MIN(order_date)
  FROM Delivery
  GROUP BY customer_id);
```

* [550. Game Play Analysis IV](https://leetcode.com/problems/game-play-analysis-iv/)

```
SELECT ROUND(COUNT(player_id)/(SELECT COUNT(DISTINCT player_id) FROM activity) , 2) AS fraction
FROM Activity 
WHERE (player_id, event_date) IN 
  (SELECT player_id, DATE_ADD(MIN(event_date), INTERVAL 1 DAY)
  FROM Activity 
  GROUP BY player_id);
```
