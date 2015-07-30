## Q221[Maximal Square](https://leetcode.com/problems/maximal-square/) 

### Solution 1 Stack,DP
#### Idea:
All idea are same with Q84&Q85. 
#### Time Complexity: 
O(mn)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public int maximalSquare(char[][] matrix) {
        int row=matrix.length;
        if(row==0) return 0;
        int col=matrix[0].length;
        int[] height=new int[col];
        int maxArea=0;
        
     for(int r=0;r<row;r++){
         for(int j=0;j<col;j++)
         if(matrix[r][j]=='1') height[j]+=1;
         else height[j]=0;
         
         Stack<Integer> s = new Stack<Integer>();
         for(int i = 0; i <= col; i++){
         	//when i==col,h=0 can pop all former
         	
            int h = (i == col ? 0 : height[i]); 
            if(s.isEmpty() || h >= height[s.peek()]){
                s.push(i);
            }else{
                int tp = s.pop();
                int side=s.isEmpty() ? i : i - 1 - s.peek();
			    maxArea=Math.max(maxArea,height[tp]>side?side*side:height[tp]*height[tp]);
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

