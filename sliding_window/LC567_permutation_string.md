## Problem 567: Permutation String
You are given two strings s1 and s2.

Return true if s2 contains a permutation of s1, or false otherwise. That means if a permutation of s1 exists as a substring of s2, then return true.

Both strings only contain lowercase letters.

```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:

        if len(s1) > len(s2):
            return False
        count1, count2 = defaultdict(int), defaultdict(int)

        #set up initial sliding window
        for i in range(len(s1)):
            count1[s1[i]] += 1
            count2[s2[i]] += 1

        def matches():
            matched = True
            for char in count1:
                if count1[char] != count2[char]:
                    matched = False
            return matched
            #can alse write this as
            #return all(count1[char] == count2[char] for char in count1)

        l = 0
        for r in range(len(s1), len(s2)):
            if matches():
                return True 

            #move the window up by 1
            count2[s2[r]] += 1
            count2[s2[l]] -= 1
            if count2[s2[l]] == 0: #clean up in case the key has no entries anymore
                del count2[s2[l]]
            l += 1
        return matches()
```
### Comments
- sliding window!!!
