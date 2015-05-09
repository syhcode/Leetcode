## Q153 [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/) 

### Solution 1: binary search in 3 situation
#### Idea: 
Like Q33,considering the three cases for rotated array,and search in each situation recursively.Analyze each cases,in 1st case A[left] is min, also we can draw a 
conclusion for the left two cases that if A[left]>A[left+1] ,A[left+1] is min or if A[right] <A [right-1], A[right] is min. 
The three cases as picture: ![](https://github.com/syhcode/Leetcode/blob/master/image/q33.jpg)
#### Time Complexity:
O(log(n))
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
       if (nums[right] <nums [right-1]) return nums[right];  

        //situation 1 :  

        if (nums[left] < nums[right])   return nums[left];
           
         
        //situation 2 : 

        else if (nums[left] < nums[mid])   return binarySearch(nums, mid, right);
              
        //situation 3

        else  return binarySearch(nums,0, mid);
           
          
    }  
}  

```
#### Reference:

---

