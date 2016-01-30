## Q329 [ Longest Increasing Path in a Matrix](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/) 

### Solution 1 DFS, Memo
#### Idea:
use a memo matrix to record the intermediate DFS result AND cut branches.
#### Time Complexity:
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public int longestIncreasingPath(int[][] matrix) {
        int m =matrix.length;
        if(m==0) return 0;
        int n = matrix[0].length;
        int max=1;
        int[][] memo = new int[m][n];
        for(int i =0;i<m;i++){
            for(int j = 0;j<n;j++){
                int temp = dfs(i,j,matrix,memo);
                max=Math.max(temp,max);
            }
        }
        return max;
    }
        public int dfs(int row,int col, int[][] matrix,int[][] memo){
            if(memo[row][col]!=0) return memo[row][col]; //cut branches
            int max=1;
            if(row+1<matrix.length && matrix[row+1][col]>matrix[row][col])
             	max=Math.max (1+dfs(row+1,col,matrix,memo),max);
            if(row-1>=0 && matrix[row-1][col]>matrix[row][col]) 
            	max=Math.max (1+dfs(row-1,col,matrix,memo),max);
            if(col+1 <matrix[0].length && matrix[row][col+1]>matrix[row][col])
            	 max=Math.max (1+dfs(row,col+1,matrix,memo),max);
            if(col-1>=0 && matrix[row][col-1]>matrix[row][col]) 
            	max=Math.max (1+dfs(row,col-1,matrix,memo),max);
            memo[row][col]=max; //record intermediate max 
            return max;
        }
}

```
#### Reference:

---

