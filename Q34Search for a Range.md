## Q34 [Search for a Range](https://leetcode.com/problems/search-for-a-range/) 

### Solution 1 Binary Search
#### Idea:
Use iterative binary search.
#### Time Complexity:
O(log(n))
#### Space Complexity:
O(1)
#### Source code:
```

public class Solution {
    public int[] searchRange(int[] nums, int target) {
        int[] result={-1,-1};
        int initial=binarySearch(nums,0,nums.length-1,target);
        if (initial==-1) return result;
        int left=initial;
        int right=initial;
        result[0]=left;
        result[1]=right;
       while(binarySearch(nums,0,left-1,target)!=-1) { //left not left end? left-1
        left=binarySearch(nums,0,left-1,target);
        result[0]=left;
       }
       while(binarySearch(nums,right+1,nums.length-1,target)!=-1){ //right not right end? right+1
        right=binarySearch(nums,right+1,nums.length-1,target); 
        result[1]=right;
       }
        return result;
    }

    public int binarySearch(int[] nums, int low,int high,int target){
        while(low<=high){
        int mid=(low+high)/2;
        if(target>nums[mid]) low=mid+1;
        else if(target<nums[mid]) high=mid-1;
        else return mid;
        }
    
        return -1;
    }
    
    
}


```
#### Reference:

---

