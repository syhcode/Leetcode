## Q73 [Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/) 

### Solution 1 
#### Idea:
In order to do in place, use first row and column to save the remained matrix "0" status,before this
record the first row and column "0" status.
#### Time Complexity:
O(m*n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {

 public class Solution {
    public void setZeroes(int[][] matrix) {
        int m=matrix.length;
        int n=matrix[0].length;
        boolean firstrow=false;
        boolean firstcol=false;
        
        for (int i=0;i<m;i++){
        if(matrix[i][0]==0)
        firstcol=true;
        }
        for(int i=0;i<n;i++){
            if(matrix[0][i]==0)
            firstrow=true;
        }
   
         for(int i=1;i<m;i++){
             for(int j=1;j<n;j++){
                 if(matrix[i][j]==0){
                     matrix[i][0]=0;
                     matrix[0][j]=0;
                 }
                 
             }
          }
       for(int i=1;i<m;i++){if(matrix[i][0]==0) setrow0(matrix,i,n); }
       for(int i=1;i<n;i++){if(matrix[0][i]==0) setcol0(matrix,i,m); }
       if(firstcol==true) setcol0(matrix,0,m);
       if(firstrow==true) setrow0(matrix,0,n);
        
   }
                   public void setrow0(int[][] matrix,int row,int n){
                       for(int i=0;i<n;i++)
                       matrix[row][i]=0;
                   }
                    public void setcol0(int[][] matrix,int col,int m){
                       for(int i=0;i<m;i++)
                       matrix[i][col]=0;
                   }
}

```
#### Reference:

---

