## Problem 76: Minimum Window Substring
Given two strings s and t, return the shortest substring of s such that every character in t, including duplicates, is present in the substring. If such a substring does not exist, return an empty string "".

You may assume that the correct output is always unique.

```python
from collections import defaultdict

class Solution:
    def minWindow(self, s: str, t: str) -> str:
        # Return early if t is longer than s
        if len(t) > len(s):
            return ""

        # Initialize frequency maps
        t_count = defaultdict(int)
        window = defaultdict(int)

        # Fill t_count with the frequencies of characters in t
        for char in t:
            t_count[char] += 1

        have, want = 0, len(t_count)  # Matches found vs required matches
        res = [-1, -1]  # Best window (start, end)
        resLen = float('inf')  # Track minimum window length

        l = 0  # Left pointer

        # Expand the window with the right pointer
        for r in range(len(s)):
            c = s[r]
            window[c] += 1

            # Increment 'have' only if the current character matches the desired frequency
            if c in t_count and window[c] == t_count[c]:
                have += 1

            # Try to shrink the window from the left while it's valid
            while have == want:
                # Update the result if a smaller window is found
                if (r - l + 1) < resLen:
                    resLen = r - l + 1
                    res = [l, r]

                # Shrink the window from the left
                window[s[l]] -= 1
                if s[l] in t_count and window[s[l]] < t_count[s[l]]:
                    have -= 1
                l += 1

        l, r = res
        # Return the result if a valid window was found, else return ""
        return "" if resLen == float('inf') else s[l:r + 1]

```
### Comments
hard
- sliding window!!!
