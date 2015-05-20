## Q59 [Spiral Matrix II ](https://leetcode.com/problems/spiral-matrix-ii/) 

### Solution 1
#### Idea:
Same with Q54,but no need to use symbol to avoid duplication.

#### Time Complexity:
O(n^2)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int[][] generateMatrix(int n) {
        int[][] matrix= new int[n][n];
                
                int input=1;
                int size=matrix.length; 
                if (size==0) return matrix;
		      
		        int level=(int)Math.ceil(size/2.);
		       
		   for(int i=0;i<level;i++){
		        
		            for(int j=i;j<size-i;j++){
		                
		               matrix[i][j]=input;
		               input++;
		                
		             
		            }
		             for(int j=i+1;j<size-i;j++){
		            	 
		           
		                matrix[j][size-1-i]=input;
		                input++;
		               
		             
		            } 
		                	
		                   for(int j=size-i-2;j>=i;j--){
		                  
		                  matrix[size-1-i][j]=input;
		                  input++;
		         
		                
		                   } 
		              
		                
		              	 for(int j=size-2-i;j>i;j--){
		                    matrix[j][i]=input;
		                    input++;
		             
		                  }
		               
		  } 
                    return matrix;
        
        
    }
}
```
#### Reference:

---

