## Q162 [Find Peak Element](https://leetcode.com/problems/find-peak-element/) 

### Solution 1
#### Idea:
Cases analyze.
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int findPeakElement(int[] nums) {
      
        
      if(nums.length==1)
            return 0;
        if (nums.length==2){
            if(nums[0]<nums[1])
            return 1;
         else
            return 0;
        }
      
       if(nums[nums.length-1]>nums[nums.length-2])
              return nums.length-1;
              
        for(int i=1;i<nums.length-1;i++){
            if(nums[i]>nums[i-1]&&nums[i]>nums[i+1])
           
           return i;
            
        }
        return 0;
        
    }
}


```
#### Reference:

---

