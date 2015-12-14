## Q74 [Search a 2D Matrix ](https://leetcode.com/problems/search-a-2d-matrix/) 

### Solution 1 Binary Search
#### Idea:
Treat it as one dimentional array.
#### Time Complexity:
O(log(min(m,n))
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
  public boolean searchMatrix(int[][] matrix, int target) {
    int row_num = matrix.length;
    int col_num = matrix[0].length;
    
    int begin = 0, end = row_num * col_num - 1;
    while(begin <= end){
        int mid = (begin + end) / 2;
        int mid_value = matrix[mid/col_num][mid%col_num];

        if( mid_value == target){
            return true;
        }else if(mid_value < target){
            //Should move a bit further, otherwise dead loop.
            begin = mid+1;
        }else{
            end = mid-1;
        }
    }
    return false;
  }
}
        		    

```
#### Reference:

---

