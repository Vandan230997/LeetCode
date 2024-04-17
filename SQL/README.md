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
select score, DENSE_RANK() over(order by score desc) as 'rank' from Scores;
```

<h3> 180. Consecutive Numbers </h3>
<h4F>Find all numbers that appear at least three times consecutively. </h4>
<h4> Solution: </h4>

```sql
select id, name
from students s
where department_id not in
(select id
from departments);
```
