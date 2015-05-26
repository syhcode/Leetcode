## Q64 [Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum/) 

### Solution 1 DP
#### Idea:
Same as Q62,two ways(up or right) can reach one position, and compare witch one is smaller.
#### Time Complexity:
O(m*n)
#### Space Complexity:
O(m*n)
#### Source code:
```
public class Solution {

  public class Solution {
    public int minPathSum(int[][] grid) {
        int m=grid.length;
        int n=grid[0].length;
        int[][] path=new int [m][n];
        path[0][0]=grid[0][0];
        
       for(int i=1;i<m;i++)
       path[i][0]=path[i-1][0]+grid[i][0];
       for(int i=1;i<n;i++)
       path[0][i]=path[0][i-1]+grid[0][i];

       for(int i=1;i<m;i++){
           for(int j=1;j<n;j++){
           
               path[i][j]=grid[i][j];
               
               if(path[i-1][j]<path[i][j-1])
              path[i][j]=path[i-1][j]+path[i][j];
               else 
              path[i][j]= path[i][j-1]+path[i][j];
           }
       }
            return path[m-1][n-1];
    }
}

```
#### Reference:

---

