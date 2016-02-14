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
    public int maxSubArray(int[] nums) { // [3,-1,-5,4]  3/3 3/2  3/0 4/4   ->4
        int sumMax=Integer.MIN_VALUE;
        int append =0;
        for(int i=0;i<nums.length;i++){
            append+=nums[i]; // 3,2,0,4
            sumMax=Math.max(sumMax,append); //3,3,3,4
            if(append<0) append=0;
        }
        return sumMax;
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
