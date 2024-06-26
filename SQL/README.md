<h2> SQL (MySQL) LeetCode Challenges Solutions </h2>

<h3> 175. Two Sum </h3>
<h4> Write a solution to report the first name, last name, city, and state of each person in the Person table. If the address of a personId is not present in the Address table, report null instead. </h4>
<h4> Solution: </h4>

```sql
SELECT p.firstName, p.lastName, a.city, a.state
FROM person p
LEFT JOIN address a
ON p.personId = a.personId
```


<h3> 176. Second Highest Salary </h3>
<h4>Write a solution to find the second highest salary from the Employee table. If there is no second highest salary, return null. </h4>
<h4> Solution: </h4>

```sql
SELECT IFNULL((SELECT distinct Salary FROM Employee ORDER BY Salary DESC LIMIT 1,1),NULL) AS SecondHighestSalary;
```


<h3> 177. Nth Highest Salary </h3>
<h4>Write a solution to find the nth highest salary from the Employee table. If there is no nth highest salary, return null. </h4>
<h4> Solution: </h4>

```sql
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN
declare A int;
set A = N-1;

  RETURN ( select nullif ((SELECT DISTINCT salary FROM Employee ORDER BY salary desc LIMIT A,1),NULL)
  );
END
```

<h3> 178. Rank Scores </h3>
<h4>Write a solution to find the rank of the scores. The ranking should be calculated according to the following rules: The scores should be ranked from the highest to the lowest. If there is a tie between two scores, both should have the same ranking. After a tie, the next ranking number should be the next consecutive integer value. In other words, there should be no holes between ranks. </h4>
<h4> Solution: </h4>

```sql
SELECT score, DENSE_RANK() OVER(ORDER by score desc) as 'rank' FROM Scores;
```

<h3> 180. Consecutive Numbers </h3>
<h4F>Find all numbers that appear at least three times consecutively. </h4>
<h4> Solution: </h4>

```sql
SELECT DISTINCT t1.num AS ConsecutiveNums
FROM logs t1
JOIN logs t2 ON t1.id = t2.id - 1
JOIN logs t3 ON t1.id = t3.id - 2
WHERE t1.num = t2.num AND t1.num = t3.num;
```


<h3> 181. Employees Earning More Than Their Managers </h3>
<h4>Write a solution to find the employees who earn more than their managers. Return the result table in any order. </h4>
<h4> Solution: </h4>

```sql
SELECT e.name AS Employee FROM Employee e
JOIN Employee m
ON e.managerId = m.id and e.salary>m.salary; 
```


<h3> 182. Duplicate Emails </h3>
<h4>Write a solution to report all the duplicate emails. Note that it's guaranteed that the email field is not NULL.
Return the result table in any order.</h4>
<h4> Solution: </h4>

```sql
SELECT DISTINCT d1.email as Email from Person d1
JOIN Person d2
ON d1.email = d2.email and d1.id != d2.id;
```



<h3>183. Customers Who Never Order </h3>
<h4>Write a solution to find all customers who never order anything. Return the result table in any order.</h4>
<h4> Solution: </h4>

```sql
SELECT name AS Customers
FROM customers
WHERE id NOT IN (SELECT DISTINCT customerId FROM orders)
```
