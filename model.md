## Q[Pascal's Triangle II](https://leetcode.com/problems/pascals-triangle-ii/) 

### Solution 1
#### Idea: except head and rear, ele[i-1][j-1]+ele[i-1][j]=ele[i][j], 
thus when get an ele[i][j],copy[i-1][j]forele[i][j+1]
#### Time Complexity:
O(K^2)
#### Space Complexity:
O(K)
#### Source code:
```
public class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> result  = new ArrayList<Integer>();
         int pre= 1;
        for(int i=0;i<rowIndex+1;i++){
            
            result.add(1);
            
            for(int j=1;j<i;j++){
                int cur  = result.get(j);               
                result.set(j, pre + cur);
                pre = cur;
            }
        }
        return result;
    }
}
```
#### Reference:

---

