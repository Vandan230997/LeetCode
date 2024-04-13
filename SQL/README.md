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

