## Problem 22: Generate Parentheses
You are given an integer n. Return all well-formed parentheses strings that you can generate with n pairs of parentheses.


```python

class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        stack = []
        res = []

        def backtrack(openN, closedN):
            #base case
            if openN == closedN == n:
                res.append("".join(stack))
                return 
            #case 1: we have less open paranthesis than n, so we can add an opening to our string
            if openN < n: 
                stack.append("(")
                backtrack(openN+1, closedN)
                stack.pop() #we remove the paranthesis because we only have one stack variable
            #case 2: we have less closed paran than open, so that means we can legally add another
            #closed paran while still keeping it valid
            if closedN < openN:
                stack.append(")")
                backtrack(openN, closedN+1)
                stack.pop()
            
        backtrack(0,0)
        return res

```
### Comments
- only add open paranthesis if open < n
- only add closed paranthesis if closed < open
- valid IFF open == closed == n
