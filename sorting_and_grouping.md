# Sorting and Grouping

* [2356. Number of Unique Subjects Taught by Each Teacher](https://leetcode.com/problems/number-of-unique-subjects-taught-by-each-teacher/)

```
SELECT teacher_id, COUNT(DISTINCT subject_id) AS cnt
FROM Teacher
GROUP BY teacher_id;
```

* [1141. User Activity for the Past 30 Days I](https://leetcode.com/problems/user-activity-for-the-past-30-days-i/)

```
SELECT activity_date AS day, COUNT(DISTINCT user_id) AS active_users
FROM Activity
WHERE (activity_date > "2019-06-27" AND activity_date <= "2019-07-27")
GROUP BY day;
```

* [1070. Product Sales Analysis III](https://leetcode.com/problems/product-sales-analysis-iii/)

```
SELECT product_id, year AS first_year, quantity, price
FROM Sales
WHERE (product_id, year) IN (
    SELECT product_id, MIN(year) AS year
    FROM Sales
    GROUP BY product_id);
```

* [596. Classes More Than 5 Students](https://leetcode.com/problems/classes-more-than-5-students/)

```
SELECT class
FROM Courses
GROUP BY class HAVING COUNT(student) >= 5
```

* [1729. Find Followers Count](https://leetcode.com/problems/find-followers-count/)

```
SELECT user_id, COUNT(follower_id) AS followers_count
FROM Followers
GROUP BY user_id
ORDER BY user_id ASC;
```

* [619. Biggest Single Number](https://leetcode.com/problems/biggest-single-number/)

```
SELECT MAX(num) AS num
FROM (
    SELECT num
    FROM MyNumbers
    GROUP BY num
    HAVING COUNT(num) = 1) AS unique_numbers;
```


* [1045. Customers Who Bought All Products](https://leetcode.com/problems/customers-who-bought-all-products/)

```
SELECT customer_id
FROM Customer
GROUP BY customer_id 
HAVING COUNT(DISTINCT product_key) = (SELECT COUNT(*) FROM Product);
```
