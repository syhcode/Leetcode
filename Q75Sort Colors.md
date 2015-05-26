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

  public class Solution {
    public void sortColors(int[] nums) {
    
       if(nums==null || nums.length<2) return;
       int low = 0; 
       int high = nums.length-1;
       for(int i = low; i<=high;) {
      
           if(nums[i]==0) {
            
            int temp = nums[i];
            nums[i] =nums[low];
            nums[low]=temp;
            i++; low++;  //i++ skip the ordered left array
           }else if(nums[i]==2) {
            
              int temp = nums[i];
              nums[i] = nums[high];
              nums[high]=temp;
              high--;  //process disoredered right array.
           }else {
               i++;
           }
       }
 

    }
}


```
#### Reference:

---

