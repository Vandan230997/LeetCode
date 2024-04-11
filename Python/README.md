<h2> Python LeetCode Challenges Solutions </h2>

<h3> 1. Two Sum </h3>
<h4> Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target. </h4>
<h4> Solution: </h4>
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        d = {}
        for i, n in enumerate(nums):
            m = target - n
            if m in d:
                return [d[m], i]
            else:
