## Q213[House Robber II ](https://leetcode.com/problems/house-robber-ii/) 

### Solution 1 DP
#### Idea:
Same as Q198, just make case analysis of nums[0] additionally.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int rob(int[] nums) {
        int len=nums.length;
        if(len==0) return 0;
        return Math.max(robLine(nums,2,len-1)+nums[0],robLine(nums,1,len));
    }
    int robLine(int[] nums,int start,int end) {
        int pre=0,cur=0;
        for(int i=start;i<end;i++){
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

