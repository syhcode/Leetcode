## Q154 [Find Minimum in Rotated Sorted Array II ](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/) 

### Solution 1: binary search in 3 situation
#### Idea: 
Just like Q81,considering the three cases for rotated array,and search in each situation recursively.Analyze each cases,in 1st case A[left] is min, also we can draw a 
conclusion for the left two cases that if A[left]>A[left+1] ,A[left+1] is min or if A[right] <A [right-1], A[right] is min.
HOWEVER, when get the same ele[left]==ele[right] or ele[left]==ele[mid],wipe out these elements by  "right-1" during binary search. 
And the three cases as picture: ![](https://github.com/syhcode/Leetcode/blob/master/image/q33.jpg)
#### Time Complexity:
O(log(n)) ~ O(n) worst case:all elements are same 
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {  
    public int findMin(int[] nums) {  
        
        int len = nums.length;  
        if (len == 0) return -1;  
        return binarySearch(nums, 0, len-1);  
    }  

    public int binarySearch(int[] nums, int left, int right) {  
       if (left == right) return nums[left];  

       int mid = (left + right) / 2;  
       if (nums[left]>nums[left+1] ) return nums[left+1]; 
       if (nums[right]<nums [right-1]) return nums[right];  
       
      // skip the duplicated non-value left(head) and right(rear) element while searching.

       if(nums[left]==nums[right]&& nums[left]<=nums[left+1])  return binarySearch(nums, left, right-1);

       if(nums[left]==nums[mid]&& nums[left]<=nums[left+1])  return binarySearch(nums, left, right-1);



        //situation 1 :  

        if (nums[left] < nums[right])   return nums[left];
           
         
        //situation 2 : 

        else if (nums[left] < nums[mid])   return binarySearch(nums, mid, right);
              
        //situation 3

        else   return binarySearch(nums,0, mid);
           
        
    }  
}  

```
#### Reference:

---

