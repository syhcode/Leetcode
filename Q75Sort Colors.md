## Q75 [Sort Colors](https://leetcode.com/problems/sort-colors/) 

### Solution 1 Two Pointers
#### Idea:
Build two array indexes low and high,from low to high,put 0 in left ordered part of array,meanwhile put 2 in right disordered part of array. 
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public void sortColors(int[] nums) {  
         if(nums.length==0) return;
         int p=0,len=nums.length;
         for(int i=0;i<nums.length;i++){
             if(nums[i]==0){
                 int temp=nums[i];
                 nums[i]=nums[p];
                 nums[p]=temp;
                 p++;
             } 
         }
         p=len-1;
         for(int i=len-1;i>=0;i--){
             if(nums[i]==2){
                 int temp=nums[i];
                 nums[i]=nums[p];
                 nums[p]=temp;
                 p--;
             } 
         }
    }
}

```
#### Reference:

---

