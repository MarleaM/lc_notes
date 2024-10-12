## Problem 53: Max Subarray
Given an integer array nums, find the 
subarray
 with the largest sum, and return its sum.

 

Example 1:

Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum 6.

Example 2:

Input: nums = [1]
Output: 1
Explanation: The subarray [1] has the largest sum 1.

Example 3:

Input: nums = [5,4,-1,7,8]
Output: 23
Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.

```python
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        current_max = 0
        overall_max = -sys.maxsize
        for num in nums:
            current_max = max(current_max + num, num)
            overall_max = max(overall_max, current_max)
        return overall_max
```
### Comments
- watch this video: https://www.youtube.com/watch?v=XwAcoLUOXcU
