# Select

* [1757. Recyclable and Low Fat Products](https://leetcode.com/problems/recyclable-and-low-fat-products/)

```
SELECT product_id
FROM Products
WHERE low_fats = 'Y' AND recyclable = 'Y';
```

* [584. Find Customer Referee](https://leetcode.com/problems/find-customer-referee/)

```
SELECT  name
FROM Customer
WHERE COALESCE(referee_id, 0) <> 2;
```

* [595. Big Countries](https://leetcode.com/problems/big-countries/)

```
SELECT name, population, area
FROM World
WHERE area >= 3000000 OR population >= 25000000;
```

* [1148. Article Views I](https://leetcode.com/problems/article-views-i/)

```
SELECT author_id as id
FROM Views
WHERE author_id = viewer_id
GROUP BY author_id
ORDER BY id ASC;
```

* [1683. Invalid Tweets](https://leetcode.com/problems/invalid-tweets/)

```
SELECT tweet_id
FROM Tweets
WHERE LENGTH(content) > 15;
```
