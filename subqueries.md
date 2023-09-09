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
```

* [1321. Restaurant Growth](https://leetcode.com/problems/restaurant-growth/)

```
```

* [602. Friend Requests II: Who Has the Most Friends](https://leetcode.com/problems/friend-requests-ii-who-has-the-most-friends/)

```
```

* [585. Investments in 2016](https://leetcode.com/problems/investments-in-2016/)

```
```

* [185. Department Top Three Salaries](https://leetcode.com/problems/department-top-three-salaries/)

```
```
