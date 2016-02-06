## Q303[Range Sum Query](https://leetcode.com/problems/range-sum-query-immutable/) 

### Solution 1 DP
#### Idea:
in order for very frequent call, record all range sum ranging from the first position in dp, 
then range(i,j) =dp[j]-dp[i-1]. 
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class NumArray {
    int[] array;
    public NumArray(int[] nums) {
        if(nums.length!=0){
            array = new int[nums.length];
            array[0]=nums[0];
            for(int i=1;i<nums.length;i++){
                array[i]=array[i-1]+nums[i];
            }
        }
    }
    public int sumRange(int i, int j) {
        if(i==0) return array[j];
        else return array[j]-array[i-1];
    }
}


```
#### Reference:

---
## Q304[ Range Sum Query 2D](https://leetcode.com/problems/range-sum-query-2d-immutable/) 

### Solution 1 DP
#### Idea:
in order for very frequent call, record all range sum ranging from the first position in dp, 
then cut out this target rectangle. 
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class NumMatrix {
    int[][] m;
    public NumMatrix(int[][] matrix) {
        int len1=matrix.length;
        if(len1>0){
            int len2=matrix[0].length;
            m=new int[len1][len2];
            m[0][0]=matrix[0][0];
            for(int row=1;row<len1;row++){
                m[row][0]=m[row-1][0]+matrix[row][0];
            }
             for(int col=1;col<len2;col++){
                m[0][col]=m[0][col-1]+matrix[0][col];
            }
            for(int j=1;j<len1;j++){
                for(int k=1;k<len2;k++){
                    m[j][k]=matrix[j][k]+m[j-1][k]+m[j][k-1]-m[j-1][k-1];
                }
            }
        }
    }
    public int sumRegion(int row1, int col1, int row2, int col2) {
        return m[row2][col2] -
        (row1==0?0:m[row1-1][col2])-
        (col1==0?0:m[row2][col1-1])+
        (row1==0||col1==0?0:m[row1-1][col1-1]);
    }
}


// Your NumMatrix object will be instantiated and called as such:
// NumMatrix numMatrix = new NumMatrix(matrix);
// numMatrix.sumRegion(0, 1, 2, 3);
// numMatrix.sumRegion(1, 2, 3, 4);


```
#### Reference:

---

