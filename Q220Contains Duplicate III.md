## Q220[Contains Duplicate III](https://leetcode.com/problems/contains-duplicate-iii/) 

### Solution 1 TreeSet,BST
#### Idea:
Use TreeSet to imply of BST, in window length in k, find ceil and floor of nums[ind] in TreeSet with height of t.
#### Time Complexity: 
O(nlogk) :
Has n Treeset to process.  
Implement of k size Treeset use logk, and check funtion(ceil or floor) of k size Treeset use logk, total nlogk.
#### Space Complexity:
O(k)
#### Source code:
```
public class Solution {
    public boolean containsNearbyAlmostDuplicate(int[] nums, int k, int t) {
        if (nums == null || nums.length == 0 || k <= 0) {
            return false;
        }

        final TreeSet<Integer> bst = new TreeSet<>();
        for (int ind = 0; ind < nums.length; ind++) {
            final Integer floor = bst.floor(nums[ind] + t);
            final Integer ceil = bst.ceiling(nums[ind] - t);
            
            if ((floor != null && floor >= nums[ind]) //rand from nums[ind]~nums[ind]+t
                    || (ceil != null && ceil <= nums[ind])) { //rand from nums[ind]-t~nums[ind]
                return true;
            }

            bst.add(nums[ind]);
            if (ind >= k) { 
                bst.remove(nums[ind - k]);
            }
        }
        return false;
    }
}

```
#### Reference:
---

