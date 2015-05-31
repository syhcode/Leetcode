## Q74 [Search a 2D Matrix ](https://leetcode.com/problems/search-a-2d-matrix/) 

### Solution 1 Binary Search
#### Idea:
Use two binary search to choose a row and search in row.
#### Time Complexity:
O(log(min(m,n))
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m=matrix.length;
        int n=matrix[0].length;
        int row;
        if(binarySearch_row(matrix,0,m-1, target)==-1) return false; // the end low>high,high=-1.
        row=binarySearch_row(matrix,0,m-1, target);
        boolean result=binarySearch( matrix, row,0,n-1,target);
        return result;
        
    }
    public int binarySearch_row(int[][] matrix, int low,int high,int target){
         while(low<=high){
	     int mid=(low+high)/2;
		 if(target>matrix[mid][0])low=mid+1;
		 else if(target<matrix[mid][0]) high=mid-1;
		 
		 else return -2; //this means the beginning is the target,find it!
	     }
	     return high;   //this index refers to the row where target exists.
   }
   public boolean binarySearch(int[][] matrix,int row, int low,int high,int target){
   		 if (row==-2) return true;
         while(low<=high){
	     int mid=(low+high)/2;
		 if(target>matrix[row][mid])low=mid+1;
		 else if(target<matrix[row][mid]) high=mid-1;
		 else return true;
	     }
			    
	     return false;
   }
}
        		    

```
#### Reference:

---

