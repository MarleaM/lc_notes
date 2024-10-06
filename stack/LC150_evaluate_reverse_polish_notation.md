## Problem 150: Evaluate Reverse Polish Notation



```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        stack = []
        for item in tokens:
            if item == "+":
                a = stack.pop()
                b = stack.pop()
                stack.append(a+b)
            elif item == "-":
                a = stack.pop()
                b = stack.pop()   
                stack.append(b-a)             
            elif item == "*":
                a = stack.pop()
                b = stack.pop()   
                stack.append(a*b)
            elif item == "/":
                a = stack.pop()
                b = stack.pop()   
                stack.append(int(b/a))
            else: #we have a number
                stack.append(int(item))
        return stack[-1]

```
### Comments
remember to cast the item back into an integer when doing division in python
