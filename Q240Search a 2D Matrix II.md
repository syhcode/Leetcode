## Q240[Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/) 

### Solution 1 Recursive 
#### Idea:
From top right, it can be seemed as a BST. 
#### Time Complexity: 
O(n+m)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m=matrix.length,n=matrix[0].length;
        return search(matrix,0,n-1,target);
    }
    boolean search(int[][] matrix,int row,int col,int target){
       if(row<matrix.length&&col>=0){
           if(matrix[row][col]>target) return search(matrix,row,col-1,target);
           else if(matrix[row][col]<target) return search(matrix,row+1,col,target);
           else return true;
       }else return false;
    }
}
```
#### Reference:
---

