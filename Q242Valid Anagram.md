## Q242[Valid Anagram](https://leetcode.com/problems/valid-anagram/) 

### Solution 1 Histogram
#### Idea:
Check two string whether contain the same char and their amount.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public boolean isAnagram(String s, String t) {
        int[] res=new int[24];
        if(s.length()!=t.length()) return false;
        for(int i=0;i<s.length();i++){
            res[s.charAt(i)-'a']++;
            res[t.charAt(i)-'a']--;
        }
        for(int i=0;i<24;i++){
            if (res[i]!=0) return false;
        }
        return true;
    }
}
```
#### Reference:
---

