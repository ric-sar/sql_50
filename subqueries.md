# Subqueries

* [1978. Employees Whose Manager Left the Company](https://leetcode.com/problems/employees-whose-manager-left-the-company/)

```
SELECT employee_id
FROM Employees
WHERE salary < 30000 AND manager_id NOT IN (
    SELECT DISTINCT (employee_id) FROM Employees
)
ORDER BY employee_id;
```

* [626. Exchange Seats](https://leetcode.com/problems/exchange-seats/)

```
SELECT ROW_NUMBER() OVER() id, student
FROM Seat
ORDER BY IF(MOD(id, 2) = 0, id-1, id+1);
```

* [1341. Movie Rating](https://leetcode.com/problems/movie-rating/)

```
(SELECT u.name AS results
FROM MovieRating r INNER JOIN Users u ON r.user_id = u.user_id
GROUP BY r.user_id
ORDER BY COUNT(r.user_id) DESC, u.name ASC
LIMIT 1)
UNION ALL
(SELECT m.title AS results
FROM MovieRatIng r INNER JOIN Movies m ON r.movie_id = m.movie_id
WHERE r.created_at LIKE '2020-02-%'
GROUP BY r.movie_id
ORDER BY AVG(r.rating) DESC, m.title ASC
LIMIT 1);
```

* [1321. Restaurant Growth](https://leetcode.com/problems/restaurant-growth/)

```
SELECT visited_on, amount, ROUND(amount/7, 2) AS average_amount
FROM (
    SELECT DISTINCT visited_on,
    SUM(amount) OVER(ORDER BY visited_on RANGE BETWEEN INTERVAL 6 DAY PRECEDING AND CURRENT ROW) as amount,
    MIN(visited_on) OVER() AS 1st_date
    FROM Customer
) AS temp
WHERE visited_on >= 1st_date + 6;
```

* [602. Friend Requests II: Who Has the Most Friends](https://leetcode.com/problems/friend-requests-ii-who-has-the-most-friends/)

```
WITH cte AS (
    SELECT requester_id AS id
    FROM RequestAccepted
    UNION ALL
    SELECT accepter_id AS id
    FROM RequestAccepted
    )
SELECT id, count(*) AS num
FROM cte
GROUP BY id
ORDER BY num DESC
LIMIT 1;
```

* [585. Investments in 2016](https://leetcode.com/problems/investments-in-2016/)

```
SELECT ROUND(SUM(tiv_2016), 2) AS tiv_2016
FROM (
    SELECT *,
    COUNT(*) OVER(PARTITION BY TIV_2015) AS CNT1,   
    COUNT(*) OVER(PARTITION BY LAT, LON) AS CNT2
    FROM Insurance) AS temp
WHERE CNT1 >= 2 AND CNT2 = 1;
```

* [185. Department Top Three Salaries](https://leetcode.com/problems/department-top-three-salaries/)

```
```
