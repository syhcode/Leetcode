## Q89[Gray Code](https://leetcode.com/problems/gray-code/) 

### Solution 1 
#### Idea:
A math job;
#### Time Complexity: 
O(2^n)
#### Space Complexity:
O(2^n)
#### Source code:
```
public class Solution {
   public  List<Integer> grayCode(int n) {
	  List<Integer> result = new LinkedList<>();
      for(int i=0;i<Math.pow(2,n);i++) result.add(i^(i>>1));
      return result;
   }
}
```
#### Reference:
---

