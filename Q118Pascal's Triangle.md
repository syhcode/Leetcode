## Q118 [Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/) 

### Solution 1
#### Idea:
except for head and rear, ele[i-1][j-1]+ele[i-1][j]=ele[i][j],and get the ele[i-1][j-1] and ele[i-1][j] from the former saved result list.

#### Time Complexity:
O(K^2)
#### Space Complexity:
O(K)
#### Source code:
```
public class Solution {
 public List<List<Integer>> generate(int numRows) {
 		List<List<Integer>> result = new ArrayList<List<Integer>>();
 		List<Integer> firstRow = new ArrayList<Integer>();
		List<Integer> preRow = new ArrayList<Integer>();
 	
 	if(numRows == 0){
 		return result;
 	}
 	
 	firstRow.add(1);
 	result.add(firstRow);
 
  for(int i = 1; i < numRows; i++){
 	
     ArrayList<Integer> curRow = new ArrayList<Integer>();
     curRow.add(1);
     preRow = result.get(i-1);
    
     for(int j = 0; j <i-1; j++){
    
      curRow.add(preRow.get(j)+preRow.get(j+1));
     }
 	
 	curRow.add(1);
    result.add(curRow);
  }
   return result;
 }

}

```
#### Reference:

---

