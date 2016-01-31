## Q290 [Word Pattern](https://leetcode.com/problems/word-pattern/) 

### Solution 1 hashmap
#### Idea:
dijection: two hashmap, take care if equals() function in comparing string.
#### Time Complexity:
O(n)
#### Space Complexity:
O(1)
#### Source code:
```
public class Solution {
    public boolean wordPattern(String pattern, String str) {
        String[] sa = str.split(" ");
        if(pattern.length()!=sa.length) return false;
        HashMap<Character,String> map1 = new HashMap<Character,String>();
        HashMap<String,Character> map2 = new HashMap<String,Character>();
        for(int i=0;i<pattern.length();i++){
            char c=pattern.charAt(i);
            String s=sa[i];
            if(!map1.containsKey(c))
                map1.put(c,s);
            else {
                if(!map1.get(c).equals(s)) return false;
            } 
            if(!map2.containsKey(s))
                map2.put(s,c);
            else {
                if(!map2.get(s).equals(c)) return false;
            }    
        }
        return true;
    }
}

```
#### Reference:

---

