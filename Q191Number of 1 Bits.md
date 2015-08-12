## Q191[Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/) 

### Solution 1 Bit Manipulation
#### Idea:
The same as Q190
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        int count=0;
        for(int i=0;i<=31;i++,n>>=1){
            if((1&n)==1) count++;
        }
        return count;
    }
}
```
#### Reference:
---

