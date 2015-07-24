## Q72[Edit Distance](https://leetcode.com/problems/edit-distance/) 

### Solution 1 DP
#### Idea:
```
Substring problem of DP with 2D matrix,Use opt[i][j] to represent the shortest edit distance
between word1[0,i-1] and word2[0, j-1]. 

Judging word1[i] and word[j], if  == , then : opt[i][j] = opt[i-1][j-1]

Otherwise we can use three operations to convert word1 to word2:

(a) if we replaced c with d: opt[i][j] = opt[i-1][j-1] + 1;

(b) if we added d after c: opt[i][j] = opt[i][j-1] + 1;

(c) if we deleted c: opt[i][j] = opt[i-1][j] + 1;
(b) and (c) have the equivalent meaning.

Find the min way approach to end of matrix. 
```
#### Time Complexity: 
O(mn)
#### Space Complexity:
O(mn) can be compress to O(n) since two lines are activated dynamically.
#### Source code:
```
public class Solution {
    public int minDistance(String word1, String word2) {
        int opt[][] = new int[word1.length()+1][word2.length()+1];
        // set basement 
        for(int i = 0;i <= word1.length();i++) opt[i][0] = i;
        for(int j = 0;j <= word2.length();j++) opt[0][j] = j;
        
        // update matrix
        for(int i = 1;i <= word1.length();i++){
            for(int j = 1;j <= word2.length();j++){
                if(word1.charAt(i-1)!=word2.charAt(j-1)){
                   opt[i][j]=1+Math.min(Math.min(opt[i-1][j],opt[i][j-1]),opt[i-1][j-1]);
                }
                else opt[i][j]=opt[i-1][j-1];
            }
        }
        return opt[word1.length()][word2.length()];
    }
}

```
#### Reference:

---

