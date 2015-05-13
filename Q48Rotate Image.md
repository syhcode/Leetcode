## Q48 [Rotate Image](https://leetcode.com/problems/rotate-image/) 

### Solution 1
#### Idea:
From the outside to the inside, sweep and swap each level ring of the matrix,each time swap 4 90-degree-related elements.
#### Time Complexity:
O(n^2)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public void rotate(int[][] matrix) {
    
        int n=matrix.length;
        
        for (int i=0; i<n/2;i++) {
        
          for (int j=i; j<n-1-i;j++){
          
            int temp = matrix[i][j];
            matrix[i][j] = matrix[n-j-1][i];
            matrix[n-j-1][i] = matrix[n-i-1][n-j-1];
            matrix[n-i-1][n-j-1] = matrix[j][n-i-1];
            matrix[j][n-i-1] =temp;
          }
          
        }

    }
}

```
#### Reference:

---

