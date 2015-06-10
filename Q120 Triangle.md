## Q120 [Triangle](https://leetcode.com/problems/triangle/) 

### Solution 1 Dynamic Programming
#### Idea: 
From the last but one row,rebuild the each row by sum of the ele's min adjacent and ele,then the first row(ele) is the solution. 
#### Time Complexity:
O(n^2)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
     public int minimumTotal(List<List<Integer>> triangle) {
        if(triangle.size() == 0)
            return 0;

        for (int i=triangle.size() - 2; i>=0; i--) {
            for (int j=0; j<=i; j++) {
            List<Integer> nextRow = triangle.get(i+1);
            int sum = Math.min(nextRow.get(j), nextRow.get(j+1)) + triangle.get(i).get(j);
            triangle.get(i).set(j, sum);
            }
        }
        return triangle.get(0).get(0);
    }

}

```
#### Reference:

---

