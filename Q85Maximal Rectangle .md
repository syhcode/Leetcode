## Q85 [Maximal Rectangle  ](https://leetcode.com/problems/maximal-rectangle/) 

### Solution 1 Stack,DP
#### Idea:  
Main algorithm is the same as Q84 Largest Rectangle in Histogram,and calculate maxArea row by row, update each
 row(height array) dynamically.
#### Time Complexity:
O(m*n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public int largestRectangleArea(int[] height) {
       public class Solution {
  public int maximalRectangle(char[][] matrix) {
        int row=matrix.length;
        if(row==0) return 0;
        int col=matrix[0].length;
        int[] height=new int[col];
        int maxArea=0;
        
     for(int r=0;r<row;r++){  //update current row elements not ignoring considering the former rows' conditions.
         for(int j=0;j<col;j++)
         if(matrix[r][j]=='1') height[j]+=1;
         else height[j]=0;
                              //calculate each row (height array) maxArea
         Stack<Integer> s = new Stack<Integer>();
         for(int i = 0; i <= col; i++){
            int h = (i == col ? 0 : height[i]);
            if(s.isEmpty() || h >= height[s.peek()]){
                s.push(i);
            }else{
                int tp = s.pop();
                maxArea = Math.max(maxArea, height[tp] * (s.isEmpty() ? i : i - 1 - s.peek()));
                i--;
            }
         }
     }    
        return maxArea;
  }
}
```
#### Reference:

---

