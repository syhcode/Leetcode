## Q84 [Largest Rectangle in Histogram ](https://leetcode.com/problems/largest-rectangle-in-histogram/) 

### Solution 1 Stack
#### Idea:  
Suppose a array is ascending, from the end of the array we can get all the possible max rectangle areas combinations.
Thus,we use stack to store the array elements ALWAYS in ASCENDING order: when meet a descending element, pop all the elements in stack former that are larger
than this element,meanwhile calculate the max areas of these popped elements(in ascending order).At the end of array, we can suppose a extra zero(smaller than any) and thus calculate the former array max rectangle area.
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public int largestRectangleArea(int[] height) {
         int len = height.length;
        Stack<Integer> s = new Stack<Integer>();
        int maxArea = 0;
        for(int i = 0; i <= len; i++){
            int h = (i == len ? 0 : height[i]);
            if(s.isEmpty() || h >= height[s.peek()]){
                s.push(i);
            }else{
                int tp = s.pop();
                maxArea = Math.max(maxArea, height[tp] * (s.isEmpty() ? i : i - 1 - s.peek()));
                i--;
            }
        }
        return maxArea;

    }
}
```
#### Reference:

---

