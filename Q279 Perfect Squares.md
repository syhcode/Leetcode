## Q279[Perfect Squares](https://leetcode.com/problems/perfect-squares/) 

### Solution 1  DP
#### Idea: 
the same as Q322 coin change, and coin is square number below n this time.
#### Time Complexity:
O(n^1.5)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public int numSquares(int n) {
        int[] dp =new int[n+1];
        for(int i=1;i<=n;i++){
            int min = Integer.MAX_VALUE;
            for(int num=1;num<=Math.sqrt(n);num++){
                int temp=num*num;
                if(i-temp>=0) min=Math.min(dp[i-temp]+1,min);
            }
            dp[i]=min;
        }
        return dp[n];
    }
}

```
#### Reference:

---

