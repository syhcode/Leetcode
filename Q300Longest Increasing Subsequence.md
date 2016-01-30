## Q300 [Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/) 

### Solution :3 pointer or DP
#### Idea:
Use 3 pointer can have n^2 time complexity However. For DP: insert numbers & cover the DP array from head in order(binary search) ,update the max length of DP array.--small number to be put in front may cause larger length.

#### Time Complexity:
O(nlogn)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public int lengthOfLIS(int[] nums) {            
        int[] dp = new int[nums.length];
        int len = 0;
        for(int x : nums) {
            int i = Arrays.binarySearch(dp,0,len, x);//not found, return -insert-1
            if(i < 0) i = -(i + 1);
            dp[i] = x;
            if(i == len) len++;
        }
        return len;
    }
}
```
#### Reference:

---

