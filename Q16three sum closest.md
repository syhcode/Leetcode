## Q16 [3 Sum Closest](https://leetcode.com/problems/3sum-closest/) 

### Solution 1
#### Idea:
Like Q15, first sort the array, then run through all of possible first element of a triplet. For each possible first element  make a  2Sum sweep of the remaining part of the array.
in order to sum close to target,for the 3 elements ,get the larger number toward right  or get the smaller number toward left ,compare the sum result and record the abs-closer-to-target result.

#### Time Complexity:
O(n^2)
#### Space Complexity:
O(1)
#### Source code:
```
 public class Solution {
    public int threeSumClosest(int[] num, int target) {
        int sum;
        int result = num[0] + num[1] + num[num.length - 1];
        Arrays.sort(num);
        for (int i = 0; i < num.length - 2; i++) {
            int low = i + 1, high = num.length - 1;
            while (low < high) {
                sum = num[i] + num[low] + num[high];
                if (sum > target) {
                    high--;
                } else {
                    low++;
                }
                if (Math.abs(sum - target) < Math.abs(result - target)) {
                    result = sum;
                }
            }
        }
        return result;
    }
  }
```
#### Reference:

---

