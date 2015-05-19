## Q123 [Best Time to Buy and Sell Stock III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/) 

### Solution 1
#### Idea:
since two transactions,divide the array into two groups,and for the first group(0~i) sweep i from 0~len-1,save the max profit for each i,later add this timing profit 
with the corresponding max profit of group(i~len-1)  in the other loop i for len-1~0 .
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution { 
    public int maxProfit(int[] prices) {
        int len = prices.length;
        int profit = 0;
       
        if (len < 2)
        return 0;
       
        int [] maxleft= new int[len];
        int min = 0;
      
        for(int i=1; i<=len-1; i++){
        
            maxleft[i] = Math.max(maxleft[i-1], prices[i] - prices[min]);
            if(prices[i]<prices[min])
             min = i;
        }
        	int max = len-1;
        	int maxright=0;
       
        for (int i=len-1; i>=0; i--){   
        
            maxright=Math.max(maxright,prices[max]-prices[i]);
            if(prices[i]>prices[max])
            max=i;
            profit = Math.max(profit, maxright + maxleft[i]);   
        }
        return profit;
    }
}


```
#### Reference:

---

