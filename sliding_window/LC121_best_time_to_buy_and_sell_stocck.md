## Problem 121: Best Time to Buy and Sell Stock
You are given an integer array prices where prices[i] is the price of NeetCoin on the ith day.

You may choose a single day to buy one NeetCoin and choose a different day in the future to sell it.

Return the maximum profit you can achieve. You may choose to not make any transactions, in which case the profit would be 0.

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        l = 0
        r = 1
        #left = buy, right = sell
        max_profit = 0
        while r < len(prices):
            #is this a profitable transaction?
            if prices[l] < prices[r]:
                profit = prices[r] - prices[l]
                max_profit = max(max_profit, profit)
            else:
                l = r
            r += 1
        return max_profit
```
### Comments
- sliding window!!!
