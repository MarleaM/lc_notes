## Problem 441: Arranging Coins
You have n coins and you want to build a staircase with these coins. The staircase consists of k rows where the ith row has exactly i coins. The last row of the staircase may be incomplete.

Given the integer n, return the number of complete rows of the staircase you will build.

```python
class Solution(object):
    def arrangeCoins(self, n):
        """
        :type n: int
        :rtype: int
        """
        #there is a formula to help with quickly summing up a series of numbers, forgot the name though
        #n/2 * (n+1)
        #we can use this concept to perform binary search
        l = 1
        r = n 
        res = 0
        while l <= r:
            mid = (l + r) // 2
            #num_coins = (mid // 2) * (mid + 1) doesn’t work because you lose precision by dividing mid too early
            num_coins = (mid * (mid+1) ) // 2
            if num_coins > n: #if the num_coins needed to create mid number of rows exceeds the amount we have 
                r = mid - 1 #move the right pointer
            else: #we have enough coins to make mid number of rows
                l = mid + 1
                res = max(res, mid) #check to see if this is the best solution to date
        return res
```
### Comments
- I was not able to fully implement Binary Search approach myself, because I was stuck at the main part of Binary Search which is -> How to decide if mid is correct value or not.
  
!!Whenever you see a pattern like!!
```
  If one value is valid, all values less than/greater than it are also valid
```
Then you can apply binary search.
