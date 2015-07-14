## Q3[Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) 

### Solution 1 HashMap
#### Idea:
Normal idea,in hashmap store the char and its position,
when find a duplicated number,abandon the elements in hashmap before this number,(use pointer "start")
update this number's new position in hashmap and begin next search.  
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int n = s.length();
        if (n == 0) return 0;

        int start = 0;
        int max = 0;
        Map<Character, Integer> lastSeens = new HashMap<Character, Integer>();
        for (int i = 0; i < n; i++) {
            Integer lastSeen = lastSeens.get(s.charAt(i));

            if (lastSeen != null)  {
                if (lastSeen >= start) {
                    max = Math.max(max, i - start);
                    start = lastSeen + 1;
                }
            }
            lastSeens.put(s.charAt(i), i);
        }
     // the final may not have duplication,just get length by end-start.
        max = Math.max(max, n - start);

        return max;
    }
}
```
#### Reference:

---

