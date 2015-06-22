## Q128 [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/) 

### Solution 1 Hashmap
#### Idea:  
Use hashmap<nums, section length> to store consecutive section,and for each consecutive section,store its length in beginning and ending hashmap <key,value>.
Each time when find and add a new consecutive element to a section meanwhile update new length in beginning and ending hashmap <key,value>.
#### Time Complexity:
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
    public int longestConsecutive(int[] nums) {
    int res = 0;
    Map<Integer, Integer> map = new HashMap<Integer, Integer>();
    for (int n : nums) {
        if (!map.containsKey(n)) {
            
            int left_len = (map.containsKey(n - 1)) ? map.get(n - 1) : 0;
            int right_len = (map.containsKey(n + 1)) ? map.get(n + 1) : 0;
            int len = left_len + right_len + 1;
            
            map.put(n, len);  //since only begin and end is valuable, this "len" can be any number.
            
            map.put(n - left_len, len);
            map.put(n + right_len, len);
            
            res = Math.max(res, len);
            
        }
        else {
            
            continue;
        }
    }
    return res;
      
    }
}
```
#### Reference:

---

