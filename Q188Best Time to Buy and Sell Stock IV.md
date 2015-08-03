## Q188[Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/) 

### Solution 1 DP
#### Idea:
Update 1~k transactions profit day after day.
#### Time Complexity: 
O(nk)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
  public int maxProfit(int k, int[] prices) {
    if(k == 0 || prices.length==0) return 0;
    int n = prices.length;        
    if(k >= n / 2) return maxProfitInf(prices);
    // balance - buy in ith price remained profit 
    
    int[] balance=new int[k + 1];
    for(int i=0;i<k+1;i++){
        balance[i]=Integer.MIN_VALUE;
    }
    int[] profit=new int[k + 1];
    
	// modify every transaction max balance and profit day by day. 	
    for(int i = 0; i < n; ++i) {
        for(int j = 1; j <= k; ++j) {                     
            balance[j] = Math.max(profit[j - 1] - prices[i], balance[j]); 
            profit[j] = Math.max(balance[j] + prices[i], profit[j]); 
        }
    }
    return profit[k];
  }
  int maxProfitInf(int[] prices) {
    int len = prices.length, profit = 0;
    for (int i = 1; i < len; i++)
            // as long as there is a price gap, we gain a profit.
      if (prices[i] > prices[i - 1]) profit += prices[i] - prices[i - 1];
    return profit;
  }

}
```
#### Reference:
---

