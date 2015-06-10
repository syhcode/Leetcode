## Q41 [First Missing Positive ](https://leetcode.com/problems/first-missing-positive/) 

### Solution 1 
#### Idea:
Rebuild the array by swapping elements, make nums[index-1]=index, flip the ele[index-1]=index,next get the target index.
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int firstMissingPositive(int[] nums) {
        int len=nums.length;
        int index=1;
         for(int i=0;i<len;i++){
            while(nums[i]>0&&i<len&&nums[i]<=len&&nums[i]!=nums[nums[i]-1]){
                int temp=nums[nums[i]-1];
               nums[nums[i]-1]=nums[i];
                nums[i]=temp;
            }
            while(index<=len&&nums[index-1]==index) 
            index++;
         }
         return index;
    }
}

```
#### Reference:

---

