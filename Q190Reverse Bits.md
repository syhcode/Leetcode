## Q190[Reverse Bits](https://leetcode.com/problems/reverse-bits/) 

### Solution 1 Bit Manipulation.
#### Idea:
Pay attention to UNSIGNED n and operator ">>>". The input overflow can regard as (int)2147483648L
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    // you need treat n as an unsigned value
    public int reverseBits(int n) {
        long result = 0L;
        for(int i=0;i<=31;i++,n>>=1){
            result<<=1;
            result|=(n&1);
        }
        return (int)result;
    }
}
```
#### Reference:
---

