## Problem 155: Minimum Stack



```python

class MinStack:

    def __init__(self):
        self.stack = []
        self.minStack = []

    def push(self, val: int) -> None:
        self.stack.append(val)
        val = min(val, self.minStack[-1] if self.minStack else val)
        self.minStack.append(val)

    def pop(self) -> None:
        self.stack.pop()
        self.minStack.pop()

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return self.minStack[-1]

```
### Comments
the val line can be broken down into an if else statement

```python
    def push(self, val: int) -> None:
        self.stack.append(val)
        if self.minStack:  # if the minStack is non-empty
            val = min(val, self.minStack[-1])  # get the minimum value between val and the top of minStack
        self.minStack.append(val)  # append only once to minStack
```
