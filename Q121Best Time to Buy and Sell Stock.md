## Q121 [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) 

### Solution 1 DP
#### Idea:
update the min of price[i] and max of profit(prices[i]-prices[min]) dynamically.
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int maxProfit(int[] prices) {
        int min=0;
     
        int profit=0;
       if (prices.length==0) return 0;
       
        for(int i=0;i<prices.length;i++){
            
        profit=prices[i]-prices[min]>profit?prices[i]-prices[min]:profit;
           
            if (prices[min]>prices[i])
                min=i;
         }
    
        return profit;
    }
}

```
#### Reference:

---

