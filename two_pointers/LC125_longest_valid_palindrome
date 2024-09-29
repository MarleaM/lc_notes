## Problem 125: Longest Valid Palindrome
Given a string s, return true if it is a palindrome, otherwise return false.

A palindrome is a string that reads the same forward and backward. It is also case-insensitive and ignores all non-alphanumeric characters.

### Code Solution:
```python
    def isPalindrome(self, s: str) -> bool:
        l, r = 0, len(s) - 1
        #solving this with two pointers will help with memory complexity
        while l < r:
            #we want to skip over non alpha-numeric characters (so like spaces, commas, etc) before we do our comparison
            while l < r and not s[l].isalnum():
                l += 1
            while r > l and not s[r].isalnum():
                r -= 1
            #have to make sure that we are comparing the lower case version of our letters
            if s[l].lower() != s[r].lower():
                return False
            l += 1
            r -= 1

        return True 
```
