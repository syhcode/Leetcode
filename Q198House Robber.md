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
    
    /*
    public int rob(int[] nums) {
        int[] res  = new int[nums.length];
        if(res.length==0) return 0;
        if(res.length==1) return nums[0];
        if(res.length==2) return Math.max(nums[0],nums[1]);
        res[0]=nums[0];
        res[1]=Math.max(nums[0],nums[1]);
        for(int i=2;i<nums.length;i++){
            res[i]=Math.max(res[i-2]+nums[i],res[i-1]);
        }
        return res[nums.length-1];
    }
    */
```
#### Reference:

---

