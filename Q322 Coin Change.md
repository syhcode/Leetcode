## Q322 [Coin Change](https://leetcode.com/problems/coin-change/) 

### Solution 1 DP
#### Idea:
dp table for 0~amount, each intermediate value search for min of coins, dp[i]=min(dp[i-coin]+1,min)
#### Time Complexity:
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public int coinChange(int[] coins, int amount) {
        if(coins.length==0) return -1;
        int dp[] = new int[amount+1];
        int temp,min;
        for(int i=1;i<amount+1;i++){ // dp[0] = 0!
            min=Integer.MAX_VALUE;
            for(int coin:coins){
                if(i>=coin && dp[i-coin]!=Integer.MAX_VALUE){
                   temp=dp[i-coin]+1; 
                   min=Math.min(temp,min);
                }
            }
            dp[i]=min;
        }
        return dp[amount]==Integer.MAX_VALUE?-1:dp[amount];
    }
}
```
#### Reference:

---

### Solution 2 backtracking + cut braches
#### Idea:
brute force for all situation,cutting braches using hashmap.
#### Time Complexity:
O(?)
#### Space Complexity:
O(?)
#### Source code:
```
public class Solution {
    int min=Integer.MAX_VALUE;
    HashMap<Integer,Integer> map =  new HashMap<Integer,Integer>();
    public int coinChange(int[] coins, int amount) {
        Arrays.sort(coins);
        helper(coins,amount,0);
        return min==Integer.MAX_VALUE? -1:min;
    }
    void helper(int[] coins, int amount,int number){
        if(amount==0){
            min=Math.min(min,number);
            return;
        }
        if(amount<0) return;
        if(map.containsKey(amount)){
            if(map.get(amount)<=number) return;
            else map.put(amount,number);
        }else map.put(amount,number);
        
        for(int i=coins.length-1;i>=0;i--){
            amount-=coins[i];
            helper(coins,amount,number+1);
            amount+=coins[i];
        }
    }
}
```
#### Reference:

---