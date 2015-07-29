## Q29[Divide Two Integers](https://leetcode.com/problems/divide-two-integers/) 

### Solution 1 Bit Manipulation
#### Idea:
The result can regard as a number building by 2's power series(binary system):Eg:17/3=4+1,Thus each time we get a most high
Order result 'digit' and deal with remained value to get lower order result 'digit'.Process iteratively.
#### Time Complexity: 
O(log(n))
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int divide(int dividend, int divisor) {
        if(dividend == Integer.MIN_VALUE && divisor == -1) 
            return Integer.MAX_VALUE;
        int sign=1;
        if(dividend>0^divisor>0) sign=-1;
        long res = 0;
        long dd = Math.abs((long)dividend);
        long dr = Math.abs((long)divisor);
        while(dd >= dr) {
            long highOrder = dr;
            long digit = 1;
            // get most high order digit.
            while((highOrder << 1) < dd) {
                digit <<= 1;
                highOrder <<= 1;
            }
            res += digit;
            dd -= highOrder;
        }
        return sign * (int)res;
    }
}
```
#### Reference:

---

