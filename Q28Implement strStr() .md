## Q28[Implement strStr() ](https://leetcode.com/problems/implement-strstr/) 

### Solution 1 KMP
#### Idea:
Depend on normal KMP algorithms.
#### Time Complexity: 
O(n)
#### Space Complexity:
O(n)
#### Source code:
```
public class Solution {
     public int strStr(String haystack, String needle) {
            if(needle.length()==0) return 0;
            if(haystack.length()==0) return -1;

            int[] prefix = prefixBuilder(needle);
            int start=0,i=0,j=0;
            while(i != haystack.length()){
                if(haystack.charAt(i) == needle.charAt(j)){
                    i++;j++;
                }else{
                    if(j==0){
                        start++;i++;
                    }else{
                        start = start+j-prefix[j-1];
                        // avoid prefix duplicated elements' matching.
                        i=start+prefix[j-1];
                        j=prefix[j-1];
                    }
                }
                if(j==needle.length())
                    return start;
            }
            return -1;
        }
        private int[] prefixBuilder(String needle){
            int[] prefix = new int[needle.length()];
            for(int i=1;i<prefix.length;i++){
                if(needle.charAt(i) == needle.charAt(prefix[i-1]))
                    prefix[i] = prefix[i-1]+1;
            }
            return prefix;
        }
}
```
#### Reference:

---

