## Q198[House Robber](https://leetcode.com/problems/house-robber/) 

### Solution 1 DP
#### Idea:
For the later element and result, consider if omit or pick current element,pass on two status,
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int rob(int[] nums) {
        int pre=0,cur=0;
        for(int i=0;i<nums.length;i++){
            int tmp=cur;
            cur=Math.max(pre+nums[i],cur);
            pre=tmp;
        }
    return cur;    
    }
}
```
#### Reference:

---

