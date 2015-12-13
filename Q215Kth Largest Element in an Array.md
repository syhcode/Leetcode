## Q215[Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) 

### Solution 1 Quick Sort
#### Idea:
Only need to sort the part whose index range including the Kth largest element's.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int findKthLargest(int[] nums, int k) {
        int start = 0, end = nums.length - 1, res = nums.length - k;
        while (start <= end) {
            int pivot = partion(nums, start, end);
            if (pivot < res) start = pivot + 1; 
            else if (pivot > res) end = pivot - 1;
            else return nums[pivot];
        }
        return nums[res];
    }

    private int partion(int[] nums, int start, int end) {
        int pivot = start, temp;
        while (start <= end) {
            while (start <= end && nums[start] <= nums[pivot]) start++;
            while (start <= end && nums[end] >= nums[pivot]) end--;
            if (start > end) break;
            temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
        }
        // nums is separated by end into two range sorted parts.  
        
        temp = nums[end];
        nums[end] = nums[pivot];
        nums[pivot] = temp;
        return end;
    }
}

```
#### Reference:

---

