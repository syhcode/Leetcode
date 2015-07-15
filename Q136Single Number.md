## Q136[Single Number](https://leetcode.com/problems/single-number/) 

### Solution 1 Bit Manipulation
#### Idea:
Since xor is commutative, just xor all elements in nums and get the single one.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int singleNumber(int[] nums) {
        int result = 0;
        for (int i = 0; i<nums.length; i++){
        result ^=nums[i];
        }
        return result;
    }
}
```
#### Reference:

---

