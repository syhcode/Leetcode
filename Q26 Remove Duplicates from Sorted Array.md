## Q26 [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) 

### Solution 1 Two Pointer
#### Idea:  
Use one pointer to  arrange the array in place, use another to skip duplicated ele finding first different ele. 
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int removeDuplicates(int[] nums) {
        int rear=0;
        int head=0;
        int len=nums.length;
        if(len==0) return 0;
        while(rear<len){
             while(nums[head]==nums[rear]){
              if(rear==len-1){
                 return ++head;
              } 
              rear++;
             }
        head++;
        nums[head]=nums[rear];       
        }
        return head;
    }
}
```
#### Reference:

---

