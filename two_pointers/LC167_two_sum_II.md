## Problem 167: Two Sum II
Given an array of integers numbers that is sorted in non-decreasing order.

Return the indices (1-indexed) of two numbers, [index1, index2], such that they add up to a given target number target 
and index1 < index2. Note that index1 and index2 cannot be equal, therefore you may not use the same element twice.

There will always be exactly one valid solution.

Your solution must use  O(1) additional space.


```python 
def twoSum(self, numbers: List[int], target: int) -> List[int]:
        l = 0
        r = len(numbers) - 1
        while l < r: #this is just modified binary search.
            current_sum = numbers[l] + numbers[r] 
            if current_sum < target:
                l += 1
            elif current_sum > target:
                r -= 1
            else: #we have found the target!!!
                return [l+1, r+1]
        return []
```
### Comments
I originally used a for loop with a binary search nested inside of it, but it did not work.
- Note: we return l+1 and r+1 because it is 1-indexed.
- Stop overthinking these questions, somethimes the answer is straightforward. Do not overthink!!!!


