## Q201[Bitwise AND of Numbers Range](https://leetcode.com/problems/bitwise-and-of-numbers-range/) 

### Solution 1 Bit manipulation
#### Idea:
The same prefix of binary system determine the result, otherwise return 0 .
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int rangeBitwiseAnd(int m, int n) {
        int res=0;
        for(int i=31;i>=0;i--){
            int tmp =1<<i;
            if((m&tmp)==0&&(n&tmp)!=0||(m&tmp)!=0&&(n&tmp)==0) break;
            else    res|=tmp&m;
        }
        return res;
    }
}
```
#### Reference:
---

