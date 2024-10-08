## Problem 139: Daily Temperatures
You are given an array of integers temperatures where temperatures[i] represents the daily temperatures on the ith day.

Return an array result where result[i] is the number of days after the ith day before a warmer temperature appears on a future day. If there is no day in the future where a warmer temperature will appear for the ith day, set result[i] to 0 instead.

```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        stack = [] #pair: [temp, index]
        res = [0]*len(temperatures) #initializing our res to be zero allows us to 
        #not have to fill in any extra zeros, since the default value is automatically zero

        for i, t in enumerate(temperatures):
            while stack and t > stack[-1][0]: #while the stack is nonempty 
            #and the temp t is greater than the temperature on the top of our stack
                stackT, stackInd = stack.pop()
                res[stackInd] = i - stackInd #how many days was it from now to the
                #next highest temperature?
            stack.append([t, i]) #when we're out of the while loop, we append to the stack the current
            #temperature and index
        return res 
```
### Comments
- This is a monotonically decreasing stack
