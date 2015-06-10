## Q53 [Maximum Subarray ](https://leetcode.com/problems/maximum-subarray/) 

### Solution 1 DP
#### Idea:
Compare all sum sections of the array,when sum<0,set sum=0 to cut sections.
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int maxSubArray(int[] nums) {
        int sum=nums[0]; 
        int result=nums[0];
        for(int i=1;i<nums.length;i++){
       
        if(sum<0) sum=0;
        sum=sum+nums[i];
        result=Math.max(result,sum);
       
        }
        return result;
    }
}

```
#### In another form:
In this way just update max-sum of sections.
```
public class Solution {
    public int maxSubArray(int[] nums) {
        int max=nums[0];
        int result=nums[0];
        for(int i=1;i<nums.length;i++){
            max=Math.max(nums[i],max+nums[i]);
            result=Math.max(result,max);
        }
        return result;
    }
}

```
#### Reference:

---
[Discuss for Divide and Conquer Solution](https://leetcode.com/discuss/694/how-solve-maximum-subarray-using-divide-and-conquer-approach)