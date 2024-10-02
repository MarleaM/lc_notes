## Problem 167: Two Sum II
Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] where nums[i] + nums[j] + nums[k] == 0, and the indices i, j and k are all distinct.

The output should not contain any duplicate triplets. You may return the output and the triplets in any order.


```python 
class Solution:
    import collections
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums.sort()
        res = []
        for i,a in enumerate(nums):
            if i > 0 and a == nums[i-1]: #it's the same value as before, we want to continue to the next iteration of the loop
                continue 
            l = i + 1
            r = len(nums) - 1
            while l < r:
                threesum = a + nums[l] + nums[r]
                if threesum < 0:
                    l += 1
                elif threesum > 0:
                    r -= 1
                else:
                    res.append([a, nums[l], nums[r]])
                    #we want to make sure that we never have a repeated value,
                    #for example, what if we had
                    #[-2, -2, 0, 0, 2, 2]
                    #when we get that first solution, we want to make sure that the next one is different
                    #but, nums[1] == nums[0], so we WOULD get the same solution. So, while it is the same
                    #we must shift the left pointer up by one. We don't have to worry about moving the right or anything
                    #because the conditions above will handle that logic for us. 
                    l += 1
                    while nums[l] == nums[l-1] and l < r:
                        l += 1
        return res
```
### Comments
We can do this in two ways. the first is by sorting first then doing the two-pointer version of two sum
or, we can do the traditional two sum way, and use a dictionary. i think this will be O(n^2) time though, so it is 
better to just do the two pointer way...
