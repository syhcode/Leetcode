## Q80 [Remove Duplicates from Sorted Array II ](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/) 

### Solution 1 Two Pointer
#### Idea:  
Same as Q35,but save and skip the first two duplicated elements.
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
	  if(len==1) return 1;
	  while(rear<len){
	  
	    if(rear<len-1&&nums[rear]==nums[rear+1]){ // save and skip the first two duplicated elements.
	     head++;rear++;nums[head]=nums[rear];
	     }
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

