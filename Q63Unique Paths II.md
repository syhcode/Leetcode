## Q63 [Unique Paths II ](https://leetcode.com/problems/unique-paths-ii/) 

### Solution DP
#### Idea:
The same as Q62, however,when meet 1 in obstacle grip,for the initial row and column initiate 0 for remained position,otherwise all 1; and for the rest iterating matrix put =0 in corresponding position,otherwise sum left and up; 
#### Time Complexity:
O(m*n)
#### Space Complexity:
O(m*n)
#### Source code:
```
public class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
       int m=obstacleGrid.length;
       int n=obstacleGrid[0].length;
       int[][] path=new int [m][n];
      
       //initiate rows
       for(int i=0;i<m;i++){  
       if(obstacleGrid[i][0]==1){path[i][0]=0; break;}
           path[i][0]=1;
       
        }
        //initiate columns   
       for(int i=0;i<n;i++){
           if(obstacleGrid[0][i]==1)  {path[0][i]=0;break;}
             path[0][i]=1;
    
        }
       for(int i=1;i<m;i++){
           for(int j=1;j<n;j++){
          
              path[i][j]=path[i-1][j]+path[i][j-1];
              if(obstacleGrid[i][j]==1) path[i][j]=0;
               
           }
       }
  
  
  return path[m-1][n-1];
  

        
    }
}
```
#### Reference:

---

