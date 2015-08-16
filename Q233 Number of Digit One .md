## Q233[Number of Digit One ](https://leetcode.com/problems/number-of-digit-one/) 

### Solution 1 Recursive
#### Idea:
When process a given n, (1)regard its first digit as a multiplier of 9, 99, or 999...'s 1-volume, (2)then append 
1-volume when 1 is as a head,(3)meanwhile count remained digit.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int countDigitOne(int n) {
         if(n <= 0)  return 0;
         int pow = 1;
         int tmp = n ;
         int headIs1 = 0;
         
         while(tmp >= 10){
            tmp /= 10;
            pow *= 10;
         }
         if( tmp > 1) headIs1 = pow; //head >1
         else  headIs1 = n%pow + 1; 
         return  tmp*countDigitOne(pow-1) + headIs1 + countDigitOne(n%pow);
    }
}
```
#### Reference:
---

