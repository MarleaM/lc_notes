## Problem 36: Valid Sudoku
You are given a a 9 x 9 Sudoku board board. A Sudoku board is valid if the following rules are followed:
- Each row must contain the digits 1-9 without duplicates.
- Each column must contain the digits 1-9 without duplicates.
- Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without duplicates.
  
Return true if the Sudoku board is valid, otherwise return false
Note: A board does not need to be full or be solvable to be valid.

### Code Solution:
```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        #create a set of nums, this makes it so that we don't have to deal with 
        #duplicates. set/dict lookup is O(1) so this is really efficient when
        #we are later looking for a value
        numSet = set(nums)
        longest = 0

        for n in nums:
            #check if its the start of the sequence
            if (n-1) not in numSet:
                #if it is the start of a sequence
                length = 0
                while (n + length) in numSet:
                    #check to see how long of a sequence it is
                    length += 1
                longest = max(longest, length)
        return longest 
```
