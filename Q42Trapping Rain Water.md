## Q42 [Trapping Rain Water ](https://leetcode.com/problems/trapping-rain-water/) 

### Solution 1 Two Pointer
#### Idea:  
Pick the smaller edge from begin and end,add the edge difference when the left(right)edge is bigger than the next right(left) edge, otherwise update the current left or right edge and pick smaller one to process then.  
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
https://leetcode.com/problems/trapping-rain-water/public class Solution {
    public int trap(int[] height) {
     int len=height.length;
     if (len < 3) return 0;
     int sum = 0;
     int l = 0, r = len - 1;

    // find the left and right edge which can hold water   
    while (l < r && height[l] <=height[l + 1]) l++;
    while (l < r && height[r] <= height[r - 1]) r--;

      while (l < r) {
        int left = height[l];
        int right = height[r];
           if (left <= right) {
            // add volum until an edge larger than the left edge
                while (l < r && left >= height[++l]){
                sum =sum+ left - height[l];
                }
           }else {
            // add volum until an edge larger than the right volum
                while (l < r && height[--r] <= right) {
                sum =sum+ right - height[r];
                }
            }
       }
    return sum;
    }
}
```
#### Reference:

---

