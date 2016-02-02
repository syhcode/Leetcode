## Q316[Remove Duplicate Letters](https://leetcode.com/problems/remove-duplicate-letters/) 

### Solution rear recursion 
#### Idea:
in searching if we meet a character that do not appear latter, the smallest character in head is found.then do recursion for remained string.aabba a abb
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public String removeDuplicateLetters(String s) {
        if(s.length()==0) return "";
        int[] a =new int[26];
        for(int i=0;i<s.length();i++){
            a[s.charAt(i)-'a']++;
        }
        int min=0;
        for(int j=0;j<s.length();j++){
            int pos =s.charAt(j)-'a';
            a[pos]--;
            if(s.charAt(j)<s.charAt(min)) min=j; //picked as head,and drop former str
            if(a[pos]==0) break;
        }
        return s.charAt(min) +
 removeDuplicateLetters(s.substring(min+1).replaceAll( ""+s.charAt(min)+"",""));
    }
}

```
#### Reference:

---

