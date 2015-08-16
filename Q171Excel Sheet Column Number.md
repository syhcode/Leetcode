## Q171[Excel Sheet Column Number](https://leetcode.com/problems/excel-sheet-column-number/) 

### Solution 1 
#### Idea:
26 counting system; 
#### Time Complexity: 
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public int titleToNumber(String s) {
        int res=0;
        for(int i=0;i<s.length();i++){
            res=res*26+s.charAt(i)-'A'+1;
        }
        return res;
    }
}
```
#### Reference:
---

