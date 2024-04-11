<h2> Pandas Python LeetCode Challenges Solutions </h2>

<h3> 2877. Create a DataFrame from List </h3>
<h4> Write a solution to create a DataFrame from a 2D list called student_data. This 2D list contains the IDs and ages of some students. </h4>
<h4> Solution: </h4>

```python
def createDataframe(student_data: List[List[int]]) -> pd.DataFrame:
    return pd.DataFrame(student_data,columns=["student_id",'age'])
```
