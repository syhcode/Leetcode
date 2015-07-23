## Q115[Distinct Subsequences](https://leetcode.com/problems/distinct-subsequences/) 

### Solution 1 DP
#### Idea:
When meet T[j]=T[i],judge T[0~j] for S[0~i] situation, we consider T[0~j-1] for s[0~i-1] situation(build new subSequence without T[j])
and consider T[0~j] for s[0~i-1] situation(append with former subSquence of s[0~i-1] with T[j]).
Process depend on a matrix. 
#### Time Complexity: 
O(mn)
#### Space Complexity:
O(mn)
#### Source code:
```
public class Solution {
  public int numDistinct(String S, String T) {
    // array creation
    int[][] mem = new int[T.length()+1][S.length()+1];

    // filling the first row: with 1s
    for(int j=0; j<=S.length(); j++) {
        mem[0][j] = 1;
    }
    for(int i=0; i<T.length(); i++) {
        for(int j=0; j<S.length(); j++) {
            if(T.charAt(i) == S.charAt(j)) {
                mem[i+1][j+1] = mem[i][j] + mem[i+1][j];
            } else {
                mem[i+1][j+1] = mem[i+1][j];
            }
        }
    }

    return mem[T.length()][S.length()];
      
  }

}

Space O(n):

public class Solution {
  public int numDistinct(String S, String T) {
    int sl = S.length();
    int tl = T.length();

    int[] dp = new int[tl+1];
    dp[0] = 1;

    for(int s=1; s<=sl; s++)
        for(int t=tl; t>=1; t--){
            if(S.charAt(s-1)==T.charAt(t-1))
                dp[t] += dp[t-1];
        }

    return dp[tl];
  }
}


```
#### Reference:

---

