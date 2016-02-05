## Q309 [Best Time to Buy and Sell Stock with Cooldown](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/) 

### Solution 1 DP
#### Idea:
using state machine analysis three status:cool,buy,sell, dynamically set their values in time sequence.
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public int maxProfit(int[] prices) {
        int n=prices.length;
        if (n <= 1) return 0;
        int[] cool = new int[n]; // no stock,can buy next time
        int[] buy = new int[n]; //hold stock, can sell or keep cool
        int[] sell = new int[n]; // no stock, can not buy next time
        cool[0] = 0;
        buy[0] = -prices[0];
        sell[0] = 0;
        for (int i = 1; i < prices.length; i++) {
            cool[i] = Math.max(cool[i - 1], sell[i - 1]);
            buy[i] = Math.max(buy[i - 1], cool[i - 1] - prices[i]);
            sell[i] = buy[i - 1] + prices[i];
        }
        return Math.max(cool[n - 1], sell[n- 1]);
    }
}
```
#### Reference:
[state machine analysis](https://leetcode.com/discuss/72030/share-my-dp-solution-by-state-machine-thinking)
---

