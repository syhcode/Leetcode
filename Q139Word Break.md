## Q139[Word Break](https://leetcode.com/problems/word-break/) 

### Solution 1 DP
#### Idea:
Mark the end position of String section matching the dictWord, judge if the String match form head to end. 
#### Time Complexity: 
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public boolean wordBreak(String s, Set<String> wordDict) {
        boolean[] dp = new boolean[s.length() + 1];
        dp[0] = true;
        for(int i=1; i < s.length()+1; i++){
            for(int j=0; j < i; j++){
                if(dp[j] && wordDict.contains(s.substring(j, i))){
                    dp[i] = true;
                    break;
                }
            }
        }
        return dp[s.length()];
    }
}
```
#### Reference:
---

