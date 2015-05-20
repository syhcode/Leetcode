## Q54 [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/) 

### Solution 1
#### Idea:
First define the matrix's level,then right->down->left->up,meanwhile in order to avoid redundant execution , set the executed status symbol of down and left,because if
a down is executed, there must be a left to execute; also up will be executed only when there is a down executed before.
#### Time Complexity:
O(m*n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
      	List<Integer> list=new ArrayList<Integer>();
      	
		        int high=matrix.length; 
		        if (high==0) return list;
		        int width=matrix[0].length;
		    
		        int temp=Math.min(high,width);
		        int level=(int)Math.ceil(temp/2.);
		        int symbol_d=0;
		        int symbol_l=0;
		       
		   for(int i=0;i<level;i++){
		        
		            for(int j=i;j<width-i;j++){
		                
		                list.add(matrix[i][j]);
		                
		             
		            }
		             for(int j=i+1;j<high-i;j++){
		            	 
		            	symbol_d=1;// the down process is executed
		                list.add(matrix[j][width-1-i]);
		               
		             
		            }  
		                if(symbol_d==1){
		                	
		                   for(int j=width-i-2;j>=i;j--){
		                   
		                  symbol_l=1; //the left  process is executed
		                  list.add(matrix[high-1-i][j]);
		         
		                
		                   } 
		                    symbol_d=0; // reset status
		                }
		                
		                if(symbol_l==1){
		                  for(int j=high-2-i;j>i;j--){
		                  list.add(matrix[j][i]);
		                
		             
		                  }
		                  symbol_l=0; //reset status
		                }
		  } 
                    return list;
        
    }
}
```
#### Reference:

---

