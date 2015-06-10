## Q35 [Search Insert Position](https://leetcode.com/problems/search-insert-position/) 

### Solution 1  Binary Search
#### Idea:  
If exists, return mid, else return low.
#### Time Complexity:
O(log(n))
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int searchInsert(int[] nums, int target) {
        int low=0;
        int high=nums.length-1;
        while(low<=high){
        int mid=(low+high)/2;
        if(target>nums[mid])low=mid+1;
        else if(target<nums[mid]) high=mid-1;
        else return mid;
        }
        return low;
    }
}
```
#### Reference:

---

