## Q97[Interleaving String](https://leetcode.com/problems/interleaving-string/) 
### Solution 1 Backtrack (TLE)
#### Idea:
Use marks to check if row and column element is enough.
#### Time Complexity: 
O()
#### Space Complexity:
O()
#### Source code:
```
public class Solution {
     boolean l=false;
     public  boolean isInterleave(String s1, String s2, String s3) {  
		if(s1.length()==0&&s2.length()==0&&s3.length()==0) return true;
		if(s1.length()+s2.length()!=s3.length()) return false;
		backtrack(0,0,0,s1,s2,s3);
		return l;
}     
	 void  backtrack(int i,int j,int k,String s1, String s2, String s3){
	    if(k==s3.length()&&i==s1.length()&&j==s2.length()) l= true;
		if(i<s1.length()&&s3.charAt(k)==s1.charAt(i)) backtrack(i+1,j,k+1,s1,s2,s3);
		if(j<s2.length()&&s3.charAt(k)==s2.charAt(j)) backtrack(i,j+1,k+1,s1,s2,s3);
		return;
	 }
			 
}  

```

### Solution 2 DP
#### Idea:
Use a 2D matrix with row s1 and  s2. matrix[i][j] means whether s3[0...i+j+1] is formed by the interleaving of s1[0...i] and s2[0...j].
Update matrix by judging if matrix[r][c] can put a element from s1 or s2 if matrix[r][c] near a 'true'.
#### Time Complexity: 
O(mn)
#### Space Complexity:
O(mn)but can make to O(n) since only two lines is activated dynamically.
#### Source code:
```
public class Solution {  
    public boolean isInterleave(String s1, String s2, String s3) {  
        
        if (s1 == null || s2 == null || s3 == null) return false;  
        if (s1.length() + s2.length() != s3.length()) return false;  
        boolean[][] dp = new boolean[s1.length() + 1][s2.length() + 1];  
        dp[0][0] = true; 
        // initiate regarding another String as null.
        for(int i = 1; i < s1.length() + 1; i++) {  
            if (s1.charAt(i - 1) == s3.charAt(i - 1) && dp[i - 1][0]) {  
                dp[i][0] = true;  
            }  
        }  
        for(int j = 1; j < s2.length() + 1; j++) {  
            if (s2.charAt(j - 1) == s3.charAt(j - 1) && dp[0][j - 1]) {  
                dp[0][j] = true;  
            }  
        }  
        for(int r = 1; r < s1.length() + 1; r++) {  
            for(int c = 1; c < s2.length() + 1; c++) {
                //consider ad moving to next level on r,judge toward down see if s1[r-1] fix.
                if (s1.charAt(r - 1) == s3.charAt(r + c - 1) && dp[r - 1][c]) {  
                    dp[r][c] = true;  
                }
                //consider as sweeping this level on c,judge toward right see if s2[c-1] fix.
                if (s2.charAt(c - 1) == s3.charAt(r + c - 1) && dp[r][c - 1]) {  
                    dp[r][c] = true;  
                }  
            }  
        }  
        return dp[s1.length()][s2.length()];  
    }  
}  

```
#### Reference:

---

