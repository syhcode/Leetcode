## Q152 [Maximum Product Subarray ](https://leetcode.com/problems/maximum-product-subarray/) 

### Solution 1 DP
#### Idea:
Same as Q53 form II,since multiplied by a negative makes big number smaller, small number bigger,thus we swap max and min when time a negative.
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int maxProduct(int[] nums) {
          int result = nums[0];

  
    for (int i = 1, max = result, min = result; i < nums.length; i++) {
        // multiplied by a negative makes big number smaller, small number bigger
        if (nums[i] < 0){
            int temp=max;
            max=min;
            min=temp;
        }

        //update bigger-product sections of array
        max = Math.max(nums[i], max * nums[i]);
        min =Math.min(nums[i], min * nums[i]);

        // choose the bigger section from the former and current sections.
       result = Math.max(result, max);
    }
    return result;

    }
}

```
#### Reference:

---

