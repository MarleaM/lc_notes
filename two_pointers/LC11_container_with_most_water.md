## Problem 11: Container with Most Water
You are given an integer array heights where heights[i] represents the height of the i'th bar.

You may choose any two bars to form a container. Return the maximum amount of water a container can store.


```python 
class Solution:
    def maxArea(self, heights: List[int]) -> int:
        l = 0 
        r = len(heights) - 1
        max_area = 0
        while l < r:
            area = min(heights[l], heights[r])*(r-l)
            max_area = max(max_area, area)
            if heights[l] < heights[r]:
                l += 1
            elif heights[r] < heights[l]:
                r -=1
            else:
                l += 1
        return max_area
```
### Comments
This one was pretty simple! 10/10.
