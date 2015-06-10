## Q27 [Remove Element ](https://leetcode.com/problems/remove-element/) 

### Solution 1 
#### Idea:
Use a index to rebuild the array deleting the value.
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int removeElement(int[] nums, int val) {
        int index=0;
        for(int i=0;i<nums.length;i++){
          if(nums[i]!=val){
            nums[index]=nums[i];
            index++;
          }
        }
   return index;
    }
}


```
#### Reference:

---

