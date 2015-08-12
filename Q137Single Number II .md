## Q137[Single Number II](https://leetcode.com/problems/single-number-ii/) 

### Solution 1 Bit Manipulation
#### Idea:
Considering binary system for each element, if a element appear 3 times, then its '1' of each digit will appear 3 times,
if not then this digit belong to the single word. 
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int singleNumber(int[] nums) {
        int res = 0;
        for (int i = 31; i >= 0; i--){
            int one = 0, pos= 1 << i;
            for (int j=0;j<nums.length;j++)
                if ((nums[j] & pos)!=0)
                    one++;
            if (one % 3==1)
                res |= pos;
            }
      
        return res;
    }
}
```
#### Reference:
---

