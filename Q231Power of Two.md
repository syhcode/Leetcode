## Q231[Power of Two](https://leetcode.com/problems/power-of-two/) 

### Solution 1 
#### Idea:
Avoid negative number.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public boolean isPowerOfTwo(int n) {
        int count=0;
        if(n<0) return false;
        while(n!=0){
          if(n%2==1) count++;
          n=n>>1;
        }
        return count==1;
    }
}
```
#### Reference:
---

