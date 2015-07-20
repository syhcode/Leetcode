## Q87[Scramble String](https://leetcode.com/problems/scramble-string/) 

### Solution Recursive
#### Idea:
Split the s1 and s2 into two sections both at index i,
find if any one of combinations of two string sections is scramble combination recursively.  
#### Time Complexity: 
O()
#### Space Complexity:
O()
#### Source code:
```
public class Solution {
    public boolean isScramble(String s1, String s2) {
        if(s1.equals(s2)) return true;
        int len=s1.length();
        int[] count=new int[26];
        for(int i=0;i<26;i++){
            count[i]=0;
        }
        for(int i=0;i<s1.length();i++){
            count[s1.charAt(i)-'a']++;
            count[s2.charAt(i)-'a']--;
        }
        for(int i=0;i<26;i++){
            if(count[i]!=0) return false;
        }
        for(int i=1;i<len;i++){
            if(isScramble(s1.substring(0,i),s2.substring(0,i))&&
               isScramble(s1.substring(i,len),s2.substring(i,len))) return true;
            if(isScramble(s1.substring(0,i),s2.substring(len-i,len))&&
               isScramble(s1.substring(i,len),s2.substring(0,len-i))) return true;
        }
        return false;
    }
}
```
#### Reference:
[String methods](http://blog.csdn.net/az44yao/article/details/7582580)
---

