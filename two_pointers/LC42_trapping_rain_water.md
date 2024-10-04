## Problem 42: Trapping Rain Water
You are given an array non-negative integers heights which represent an elevation map. Each value heights[i] represents the height of a bar, which has a width of 1.

Return the maximum area of water that can be trapped between the bars.


```python 
class Solution:
    def trap(self, height: List[int]) -> int:
        l = 0
        r = len(height) - 1
        leftMax, rightMax = height[l], height[r]
        res = 0
        while l < r: #before they meet each other
            if leftMax < rightMax: #we want to shift the left pointer
                l += 1
                leftMax = max(leftMax, height[l]) #we only care about the height of left
                #since the minimum is required to compute the max area that we can fill with water
                res += leftMax - height[l]
            else: #we want to shift the right pointer
                r -= 1
                rightMax = max(rightMax, height[r]) #same type of logic here
                res += rightMax - height[r]
        return res
```
### Comments
