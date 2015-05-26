## Q209 [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/) 

### Solution 1 Two Pointers
#### Idea:
Use two pointers to constrain the length of Subarray(a continuous cut-set of the array ),compare the each length.
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {

  public class Solution {
    public int minSubArrayLen(int s, int[] nums) {
 
        int start = 0, end = 0, sum = 0;
        int minLen = nums.length+1;//all possible no more than this value.
        
        while (end < nums.length) {
            
            while (end < nums.length && sum < s) sum += nums[end++];
            if (sum < s) break;
            while (sum >= s) sum -= nums[start++];
            if (end - start + 1 < minLen) minLen = end - start + 1;
        }
        return minLen == (nums.length+1) ? 0 : minLen;
    }
}
    


```
#### Reference:

---
[Two AC solutions in Java with time complexity of N and NLogN with explanation] (https://leetcode.com/discuss/35378/solutions-java-with-time-complexity-nlogn-with-explanation)
