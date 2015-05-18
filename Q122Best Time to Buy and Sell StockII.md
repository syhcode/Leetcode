## Q122 [Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/) 

### Solution 1 DP
#### Idea:
Since can buy and sell this stock for many times, the max profits should be the sum of all possible profits produced from balance of every two neighbors.
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int maxProfit(int[] prices) {
           
        int profit=0;
       if (prices.length==0) return 0;
       
        for(int i=1;i<prices.length;i++){
                       
            if (prices[i]>prices[i-1])
                
            profit+=prices[i]-prices[i-1];
         }

      return profit;
    }
}

```
#### Reference:

---

